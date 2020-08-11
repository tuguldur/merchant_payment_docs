МОСТ Финтек ХХК-ын явуулдаг үйлчилгээний талаар www.most.mn хаягаар хандаж ерөнхий мэдээлэл авах боломжтой.

Нээлттэй API-ын загварыг эндээс харж болно. http://202.131.242.165:9088/help

Холболтын документ: https://drive.google.com/file/d/1He_lhIuIFjpbLdl35X0q1SZGetewMHxR/view?usp=sharing
<br>
URL: http://202.131.242.165:9089/api/mapi/TT3051 --QR create
<br>
URL: http://202.131.242.165:9089/api/mapi/TT3065 -- QR check
<br>
URL: http://202.131.242.165:9089/api/mapi/TT1608 -- TAN create

##### srcInstId, posNo, payeeId талбаруудыг МОСТ руу хандаж авна уу. info@most.mn

#### Жишээ:

```javascript
var myHeaders = new Headers();
myHeaders.append("PV", "05");
myHeaders.append("TT", "3051");
myHeaders.append("RS", "00");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  SD: "tVWQIAIXxyBxV4RJmGIGkek7uTu8Ap2cJQnqpPPJNuM=",
  EK:
    "KfbsuGZKsq1gM3an6JdA6LQny/8hjKkYa6eQot/tAE/aEGOwLWJOxKsZsQ2bvxHv/T7VZLuEF3eS1CGyxZQmRsjQaNfh36kA9MVQUe2zXtA1kRMNb6H8YXACVhe4Snx0SbEztFnMXt9uskA7iEwcnW/lpaRkwxmhbh3NiNjlCSw=",
  SG: "MPdUd+c0jdmdpir6FIfBRKSO3T8=",
  srcInstId: "20200318",
  channel: "44",
  lang: "0",
  traceNo: "2020052703472500",
  tranCur: "MNT",
  tranAmount: "5000",
  billId: "Google.com",
  posNo: "60883",
  payeeId: "60883",
  tranDesc: "test",
  qrPaidLimit: "1",
  deviceIp: "",
  deviceMac: "",
  deviceName: "",
  PbKA:
    "&lt;RSAKeyValue&gt;&lt;Modulus&gt;n0GT9szLkGl6ST349vqiMqXnYOv0S64FKmtecYFxztDHy89baEezBNtefeHGLKtFCWehshLoqd/ClYb0zm/A2Jhbxc6+nHeJCw3jLsh9qJsgyg2qYcTYxUEA3UCOIz0uHu6BRB+ZQpASAn1jN1OFAQeP3CaIEy2+QxWZHKPHkNE=&lt;/Modulus&gt;&lt;Exponent&gt;AQAB&lt;/Exponent&gt;&lt;/RSAKeyValue&gt;",
});
var requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow",
};
fetch("http://202.131.242.165:9089/api/mapi/TT3051", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

#### Response

```json
{
  "responseCode": "0",
  "responseData": "{\"qpay_account_id\":\"18959\",\"qr_image\":\"\",\"qr_code\":\"77296678945702020081122082382016015000000000019136\"}",
  "responseDesc": "QR code is generated.",
  "traceNo": "2018062504070707"
}
```

Test MostMoney apk: <br>
Нэвтрэх 99008305 | 99008305 <br>
Пин 1245 <br>
Гүйлгээ амжилттай хийвэл мост-с танай руу гүйлгээний мэдээлэл Webhook-р явуулах юм. Тэгэхээр төлбөрийн мэдээлэл хүлээж авах хаяг өгөх хэрэгтэй танайхаас.

#### Example webhook

```xml
<data>
    <retType>0</retType>
    <retDesc>Success</retDesc>
    <paymentId>4085</paymentId>
    <bankTxnId>28203920</bankTxnId>
    <bankTxnDate>2020-04-09 09:17:53</bankTxnDate>
    <amount>415000</amount>
    <billId>2020040909212148|3</billId>
</data>

2020-04-09 09:18:15.754 [346] SIGN:

<data>
    <retType>0</retType>
    <retDesc>Success</retDesc>
    <paymentId>4085</paymentId>
    <bankTxnId>28203920</bankTxnId>
    <bankTxnDate>2020-04-09 09:17:53</bankTxnDate>
    <amount>415000</amount>
    <billId>2020040909212148|3</billId>
    <Signature xmlns=&quot;http://www.w3.org/2000/09/xmldsig#&quot;>
        <SignedInfo>
            <CanonicalizationMethod Algorithm=&quot;http://www.w3.org/TR/2001/REC-xml-c14n-20010315&quot;/>
            <SignatureMethod Algorithm=&quot;http://www.w3.org/2000/09/xmldsig#rsa-sha1&quot;/>
            <Reference URI=&quot;&quot;>
                <Transforms><Transform Algorithm=&quot;http://www.w3.org/2000/09/xmldsig#enveloped-signature&quot;/></Transforms>
                <DigestMethod Algorithm=&quot;http://www.w3.org/2000/09/xmldsig#sha1&quot;/>
                <DigestValue>FOorFt71eWeq1OwR7z//3k9Zc+w=</DigestValue>
            </Reference>
        </SignedInfo>
        <SignatureValue>TI9EPAntquXN8qpavtbdXemCKlPHuyQRxgqKQwKg/eL4eJelcq+VLUBYVEeKThJ9VwnmOTlU4bbhAOKF66vhaiGwqYlesh/5Rd/d1nOrlqkm2lla8cL7kwWo8dakgcQe+EkFW1Ykdb8W988Om8doy+SDQX5yo49LPwSjEz+LhvGCHjyX4vEW+5kzTmYnVaqUEGxHPqeUOIdYiSIoTO5RAcMJKtbQC+RfbUEyWscartmU71I2GiX8vxCPMSBQwX1zd3YQzXG7bf7GUXm7JqLEE6iOfo6sUwckSD8vlZCsA/EPitz2torSZfwFeB8ev9UOYweqCABGi2q2112RlxjLvQ==</SignatureValue>
        <KeyInfo>
            <KeyValue>
                <RSAKeyValue>
                <Modulus>tGdklLSpIV1MhYzzP1Y4w8DJXLiR/Jkz1TL/0BGV6OtfevU0OVJVOYd3MgOvcnGPnFg1+zruR4JA5uvpJqMBoG91dmfeIqlTYg7Gw9r7zeAjECSCSBWhNVt+kHyfhcUczEBh5NeEbY8QO9hImiLeaHov9O5EXIRbOozMdkjG9KiEVz3fliDRbNJn8S+GaPQLF1KiN1Z4jds3LZUV7exDFrv4XF9d1oNo5oU/bHRcV41He63WbKQFgXwaczCI3eu+c6MQGsKmkQChMDle3fIL0txyvx60sbbXstzB5VL61phqC7TayGK67nbLEHIB497R5WnxouOiAJgjbLyrP+Whrw==</Modulus>
                <Exponent>AQAB</Exponent>
                </RSAKeyValue>
            </KeyValue>
        </KeyInfo>
    </Signature>
</data>
```
