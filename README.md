# 实惠小程序（房屋）

## 1. 如何运行

1. 全局安装或更新WePY命令行工具
```bash
$ npm install wepy-cli@1.7.1 -g
```
2. 全局安装sass,less
```bash
$ npm install sass -g
$ npm install less -g
```
3. 进入项目目录，安装依赖
```bash
$ npm install
```
4. 开始开发
```bash
$ npm run dev
```
5. 预览效果
在微信开发者工具中选择小程序项目，项目目录选择本项目的dist文件夹
-----------

## 2. 重要提醒

1. 使用微信开发者工具-->添加项目，项目目录请选择dist目录。
2. 微信开发者工具-->项目-->关闭ES6转ES5。 **重要：漏掉此项会运行报错。**
3. 微信开发者工具-->项目-->关闭上传代码时样式自动补全。 **重要：某些情况下漏掉此项也会运行报错。**
4. 微信开发者工具-->项目-->关闭代码压缩上传。 **重要：开启后，会导致真机computed, props.sync 等等属性失效。**
5. 本地项目根目录运行`wepy build --watch`，开启实时编译。（注：如果同时在微信开发者工具-->设置-->编辑器中勾选了文件保存时自动编译小程序，将可以实时预览，非常方便。）
6. **请注意开发中eslint相关报错并解决，感谢。**
7. 项目引入了editorconfig以统一代码书写格式，vscode可搜索安装`EditorConfig for Visual Studio Code`插件，webstorm默认支持editorconfig。
8. ESLint规则建议协商后统一修改。
------------

## 3. 代码高亮
  [点击查看](https://tencent.github.io/wepy/document.html#/?id=%e4%bb%a3%e7%a0%81%e9%ab%98%e4%ba%ae)

--------------

## 4. 开发过程
```shell
# 1. 开发
$ npm run dev
# 真机预览先build再上传代码
# 新建标准页面  npm run new:page pageName

# 2. 发布
# i. src/util/constants.js   HOST切换为 https://napi.hiwemeet.com
# ii. src/app.wpy  全局变量 isProd切换为true
$ npm run build
```

### 版本号约定
提交体验版时

如本期开发版本为2.0.0，则第一次体验版版本号为2.0.0.a.1，修改bug发新的体验版时一次增加最后一位的数值(2.0.0.a.2,2.0.0.a.3)

a代表alpha


---------


## 5. 接口API
### v2.0.0  (2018-03-29上线,story/946)
API | 开发人员
--- | ----
[查询搜索条件](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/2345424800app/get_app_rent_search) | 王慧敏
[出租列表](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/2345424800app/get_app_rent_search) | 王慧敏
[二手房列表](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/2345424800app/get_app_sales_search) | 王慧敏
[依据城市查询区域信息](http://test.api.docs.17shihui.com/detail.html?url=http://test.paas.api.intra.hiwemeet.com/swagger.json#!/304652406621306/region_districts) | 杨琦
[依据汉字城市名查询城市ID](http://test.api.docs.17shihui.com/detail.html?url=http://test.paas.api.intra.hiwemeet.com/swagger.json#!/304652406621306/region_completeCityInfo) | 杨琦
[小区信息查询](http://test.api.docs.17shihui.com/detail.html?url=http://test.paas.api.intra.hiwemeet.com/swagger.json#/) | 杨琦
[获取服务中心拿400电话](http://test.api.docs.17shihui.com/detail.html?url=http://test.paas.api.intra.hiwemeet.com/swagger.json#!/mobile5826381211532001324515/) | 杨琦
[查询400电话](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/20844208492596825454/) | 何知浩
[广告banner接口](http://test2.api.hiwemeet.com/advertisement/swagger-ui.html#!/app-controller-v-2/propertyBannerListUsingGET_1) | 袁衷述
[房源推荐列表](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/app/get_wechat_clue_house) | 夏波
[房源详情](http://test.api.docs.17shihui.com/detail.html?url=http://test.papi.hiwemeet.com/house/swagger.json#!/app/get_wechat_clue_house_id_0_9) | 夏波
[获取18个可切换城市](http://test2.api.hiwemeet.com/sh/address/get18City) | 王林
[获取18个可切换城市（分组）](http://test2.api.hiwemeet.com/sh/address/getCityGroupByLetter) | 王林

------------

## 6. 开发注意事项
1. 房源详情页存在分享 pages/houseDetail/index, 请不要依赖本地数据存储
2. app的显示逻辑严重依赖本地存储的address，communityId等字段，请谨慎修改

-----------

## 7. 数据上报
数据格式
```json
{
  "time": "2018-01-01 12:00:00", // 时间
  "appid": 1, // 固定为 1
  "deviceid": "", // 设备标识
  "os": "Android/iOS", // 操作系统
  "storeid": 1234, // 小区ID
  "source": "", // 来源
  "uid": 1234, // 用户ID
  "event": "", // 事件
  "page": "", // 页面
  "expand": {} // 扩展字段
}
```

-----------

## 8. 业务介绍
### 8.1 页面
页面目录 | 页面描述 | 页面路径 | 页面参数 | 备注
------ | ------- | ------- | ------- | ----
src/pages/house | 房屋首页 | pages/house/index | 扫码进入时传小区ID | 每次打开时，依据经纬度获取位置信息，并存入本地address，扫码进入的用户存储小区ID
src/pages/switchCity | 切换城市页 | pages/switchCity/index | 无 | 切换城市后，会清除本地存储的小区ID，使得扫码进入的用户恢复到与普通用户相同的状态
src/pages/usedHouse | 二手房列表页 | pages/usedHouse/index | 无 | 若本地存储小区ID，则第一次查询使用小区作为查询条件
src/pages/rentalHouse | 租房列表页 | pages/rentalHouse/index | 无 | 同上
src/pages/houseDetail | 房源详情页 | pages/houseDetail/index | 房源ID,房源类型 | 此页面存在分享逻辑，所以参数只依赖路由传参，不要使用本地存储信息
src/pages/webView | webView页 | pages/webView/index | webview的url | 小程序使用自定义navigation,所有在小程序内打开的网页需要适配小程序在页面顶部添加返回按钮

### 8.2 本地存储
key | 示例 | 描述
--- | --- | ----
communityId | 427158 | 用户扫描小区二维码时会在本地存储
address | { city: '上海', cityId: 1 } | 定位或依据小区ID查询后存储在本地
isNotFirst | true | 用户只要打开过一次房屋首页就会置为true

-----------

## 9. UI库及其他组件开发情况
### 9.1 Faiz
目前放在src/faiz路径中，开发完毕后会迁移到npm上

1. Dialog 对话框组件(房屋首页有使用)
2. navBar 导航栏组件(列表页，房源详情页均使用)
3. popup 弹出层组件(房屋首页有使用)
4. statusBar 状态栏统一组件(各页面均有使用)
5. card 卡片(推荐列表，租房，二手房列表项有使用)
6. panel (房屋首页，详情页有使用)
7. color.scss (字体颜色)
8. helper.scss(字号，flex，溢出隐藏)

### 9.2 项目本身的组件
1. ecCanvas 引入eCharts（房源详情有使用）
2. mixin(setAddress) 定位并查询对应城市的相关信息（房屋首页及切换城市页有使用）

-----------

## 10. 待办
1. [] npm run dev 的时候部指定部分文件不编译，直接复制
2. [] 抽离servise
3. [] 引入字体图标
4. [] 封装列表组件
5. [] 封装占位图image，封装依据imgId显示图片的image
6. [] 补充Faiz文档及示例

------------
## 11. 参考文献及资料
- [WePY文档](https://tencent.github.io/wepy/index.html)
- [小程序开发文档](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html)
- [微信开发者社区](https://developers.weixin.qq.com/)
