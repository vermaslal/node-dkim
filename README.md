# DKIM Signer

Sign RFC822 messages with DKIM. This module is extracted from [dkim-signer](https://github.com/andris9/dkim-signer).

## Usage

```javascript
// require signer function
var DKIMSign = require("node-dkim").DKIMSign;

// generate a RFC822 message
var rfc822message = "Subject: test\r\n\r\nHello world";

// setup DKIM options
var dkimOptions = {
    domainName: "example.info",
    keySelector: "dkim",
    privateKey: require("fs").readFileSync("./test_private.pem")
};

// generate signature header field
var signature = DKIMSign(rfc822message, dkimOptions);

// join signature header field with the message
console.log(signature + "\r\n" + rfc822message);
```



## Another Uses



```javascript
// require signer function
var DKIMSigner = require("node-dkim").DKIMSigner;
var fs=require('fs');
// generate a RFC822 message
var rs=fs.createReadStream(filePath)
var ws=fs.createWriteStream(fileDestPath)

// setup DKIM options
var dkimOptions = {
    domainName: "example.info",
    keySelector: "dkim",
    privateKey: require("fs").readFileSync("./test_private.pem")
};

// generate signature and write to another file


rs.pipe(new DKIMSigner(dkimOptions)).pipe(ws);

```



## License

**MIT**
