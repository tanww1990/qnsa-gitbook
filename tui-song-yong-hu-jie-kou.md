# 推送用户接口

---

**简要描述：**

```
    去哪上岸平台用户注册并完善资料，申请平台产品订单后，会调用该接口为合作平台推送用户
```

**请求URL：**

```
    平台方提供
```

**请求方式：**

```
    POST
    Content-Type：application/json;charset=utf-8
```

**参数：**

|  | 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| header | clientId | 是 | String | 固定为THIRDPARTY\_QUNADAI |
| header | clientTime | 是 | String | 请求发送时的时间 |
| header | s | 是 | String | md5签名=md5Hex\(clientId + clientTime + bodyString + key\) |
| body | data | 组合 | json |  |
| body | phone | 是 | String | 手机号码 |
| body | idNum | 是 | String | 身份证号 |
| body | name | 是 | String | 姓名 |
| body | wechat | 是 | String | 微信号 |
| body | qq | 是 | String | QQ号 |
| body | eduLevel | 是 | String | 教育程序: 硕士及以上、本科、大专、中专/高中及以下 |
| body | province | 是 | String | 省份 |
| body | city | 是 | String | 城市 |
| body | district | 是 | String | 区 |
| body | address | 是 | String | 具体地址 |
| body | socialInsurancePayed | 是 | Integer | 是否缴纳社保（0否1是） |
| body | emergencyContactName | 是 | String | 紧急联系人姓名 |
| body | emergencyRelation | 是 | String | 紧急联系人关系: 配偶、 父母、兄弟姐妹、子女、同事、同学、朋友 |
| body | emergencyContactPhone | 是 | String | 紧急联系人电话 |
| body | zhimaScore | 是 | Integer | 芝麻分 |

参数说明：

clientId：为固定值\(THIRDPARTY\_QUNADAI\)；

clientTime：为时间戳\(System.currentTimeMillis\(\)\)；

签名加密md5：org.apache.commons.codec.digest.DigestUtils.md5Hex\(\)；

key：合作平台方提供。

**请求示例\(**bodyString**\)：**

```
           {
              "data": "{
                      "phone": "18698574854",
                      "idNum": "45215919990301502X",
                      "name": "李测试",
                      "wechat": "24554658465",
                      "qq": "2455465",
                      "eduLevel": "本科",
                      "province": "广东省",
                      "city": "佛山市",
                      "district": "南海区",
                      "address": "测试地址",
                      "socialInsurancePayed": "1",
                      "emergencyContactName": "测试他妈",
                      "emergencyRelation": "同学",
                      "emergencyContactPhone": "13432499954",                                          
                      "zhimaScore": "750"
                      }"
              }
```

**返回示例：**

```
{
    "status": "1",
    "msg": "推送成功",
    "data": {
        "appDownloadUrl": "https://wap.qunadai.com"
    }
}
```

**返回参数说明：**

| 参数名 | 二级参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| status |  | 是 | String | 状态：1-成功，0-失败 |
| msg |  | 是 | String | 返回描述 |
| data |  |  |  |  |
|  | appDownloadUrl | 否 | String | 申请合作平台产品后需要跳转的h5地址，如无需跳转返回null |



