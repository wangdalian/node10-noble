这个是提供的E1000/X1000/X2000 Container Node >= 8.0 版本下使用noble的示例
Node 6.x版本可以直接安装使用，无此问题

因为使用官方的noble包，在Node >= 8.0的环境中使用时，直接安装会报错，参考此链接修改代码内容：
https://github.com/noble/node-bluetooth-hci-socket/pull/91/commits/462e332cfa92da7d4e7dc610826c923f104b1dad

另外修改bluetooth-hci-socket包中的Lib/native.js中部分代码，因为编译库的路径问题找不到编译出的库

这个示例中并没有集成编译好的binding.node二进制，如果需要使用编译好的二进制，可以参考这个项目中的bleno的使用方式，底层都是依赖bluetooth-hci-socket库：
https://github.com/AcaciaNetworks/toB/tree/dev_wqa/MOT


另外如果修改了bluetooth-hci-socket中的代码，请记得手动清除以下文件，否则不会触发重新编译（TODO: 待优化处理）
```
rm -rf ./node_modules
rm -rf ./package-lock.json
rm -rf packages/noble/bluetooth-hci-socket/node_modules/
rm -rf packages/noble/bluetooth-hci-socket/package-lock.json
```
