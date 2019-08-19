# 跨平台支持

核心需要跨平台兼容的地方有两处：

- transports
- integrations/globalhanders

## transports

request

- [微信小程序 wx.request()](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html)
- [字节跳动小程序 tt.request()](https://developer.toutiao.com/docs/api/request.html#request)
- [支付宝小程序 my.request()](https://docs.alipay.com/mini/api/owycmh)

## integrations/globalhanders

错误监听函数

- [微信小程序 App.onError(String error)](https://developers.weixin.qq.com/miniprogram/dev/reference/api/App.html)
- [微信小程序 wx.onError(function callback)](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.onError.html)
- [字节跳动小程序 App.onError(msg)](https://developer.toutiao.com/docs/framework/startupApp.html)
- [字节跳动小程序 tt.onError(function callback)](https://developer.toutiao.com/docs/game/system/system-event/tt.onError.html)
- [支付宝小程序 App.onError(msg)](https://docs.alipay.com/mini/framework/app)
- 支付宝小程序不支持 my.onError(function callback)

页面不存在监听函数

- [微信小程序 App.onPageNotFound(Object object)](https://developers.weixin.qq.com/miniprogram/dev/reference/api/App.html)
- [微信小程序 wx.offPageNotFound(function callback)](https://developers.weixin.qq.com/miniprogram/dev/api/base/app/app-event/wx.offPageNotFound.html)
- [字节跳动小程序 App.onPageNotFound(res)](https://developer.toutiao.com/docs/framework/startupApp.html)
- 字节跳动小程序不支持 tt.onPageNotFound()
- 支付宝小程序两种方式均不支持

监听内存不足的告警事件

- [微信小程序 wx.onMemoryWarning(function callback)](https://developers.weixin.qq.com/miniprogram/dev/api/device/performance/wx.onMemoryWarning.html)
- [字节跳动小程序 暂不支持](https://developer.toutiao.com/docs/game/performance/onMemoryWarning.html)
- [支付宝小程序 my.onMemoryWarning()](https://docs.alipay.com/mini/api/hszexr)

## 总结

| | 微信 | 字节跳动 | 支付宝 |
| -- | -- | -- | -- |
| request | ✔️| ✔️| ✔️|
| App.onError | ✔️| ✔️| ✔️|
| App.onPageNotFound | ✔️| ✔️| × |
| onError | ✔️| ✔️| × |
| onPageNotFound | ✔️| × | × |
| onMemoryWarning | ✔️| × | ✔️|

由于字节跳动小程序和支付宝小程序对调用 API 监听异常的支持度不高，所以决定仅微信小程序平台支持默认监听方式上报异常，其他平台均需要在在实际项目中的 App() 主动上报异常。