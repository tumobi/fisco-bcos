# FISCO BCOS Node.js SDK

Node.js SDK为联盟链平台 [FISCO BCOS](https://github.com/FISCO-BCOS/FISCO-BCOS/tree/master) 提供面向Node.js语言的应用程序接口，使用 Node.js SDK 可以简单快捷地开发基于 FISCO-BCOS 的 Node.js 应用。Node.js SDK **仅支持** v2.0.0 及以上版本的 [FISCO BCOS](https://github.com/FISCO-BCOS/FISCO-BCOS/tree/master)。


## 一、文档说明
本项目基于 [FISCO-BCOS/nodejs-sdk](https://github.com/FISCO-BCOS/nodejs-sdk) 修改，并删除了 cli 部分，具体使用请查[看官方文档](https://github.com/FISCO-BCOS/nodejs-sdk)。

## 二、使用示例
安装 fisco-bcos sdk
```
npm install fisco-bcos --save
```
创建配置文件 config.json
```
{
    "encryptType": "ECDSA",
    "accounts": {
        "mmt": {
            "type": "pem",
            "value": "./accounts/xxx.pem"
        }
    },
    "nodes": [
        {
            "ip": "127.0.0.1",
            "port": "20200"
        }
    ],
    "authentication": {
        "key": "./sdk/sdk.key",
        "cert": "./sdk/sdk.crt",
        "ca": "./sdk/ca.crt"
    },
    "groupID": 1,
    "chainID": 1,
    "timeout": 30000
}
```

使用方法
```
const fisco = require('fisco-bcos');
const path = require('path');

const config = new fisco.Configuration(path.resolve('./config.json'));
const webj3 = new fisco.Web3jService(config);

(async () => {
  const result = await webj3.getTotalTransactionCount();
  console.log(result);
})();
```


## 三、License

Node.js SDK 的开源协议为 [APACHE LICENSE, VERSION 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt)，详情请参考 [LICENSE](./LICENSE)。
