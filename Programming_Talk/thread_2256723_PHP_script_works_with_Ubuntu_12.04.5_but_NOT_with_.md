---
title: "PHP script works with Ubuntu 12.04.5 but NOT with Ubuntu 14.04"
date: 2014-12-14
forum: Programming Talk
---

### Post by Gokhan_CP on 2014-12-14
I have the following snippet in my code:

[PHP]    
$objCurl = curl_init();    
curl_setopt($objCurl, CURLOPT_SSL_VERIFYHOST, FALSE);    
curl_setopt($objCurl, CURLOPT_RETURNTRANSFER, 1);   
curl_setopt($objCurl, CURLOPT_CUSTOMREQUEST, "POST");    
curl_setopt($objCurl, CURLOPT_SSL_VERIFYPEER, FALSE);    
curl_setopt($objCurl, CURLOPT_SSLVERSION, 1);    
$time = time();    
curl_setopt($objCurl, CURLOPT_URL, 'https://ms.website.com:443' . $this->requestServices . $this->createString($this->mbPurchase, ($itemId)));    
$strResponse = curl_exec($objCurl);
[/PHP]

It always SUCCESSFULLY executes on my Ubuntu 12.04.5 server, however, I always get a "SSL Protocol Error" on Ubuntu 14.04.

Is there anything I can do to make this script work on my Ubuntu 14.04 server as well? Because of this, I have been paying for two servers recently.

Please refer to this if you are wondering what the error looks like: [http://stackoverflow.com/questions/27414592/php-curl-unknown-ssl-protocol-error-in-connection-to](http://stackoverflow.com/questions/27414592/php-curl-unknown-ssl-protocol-error-in-connection-to)

---

### Post by Sasha_Aderolop on 2014-12-17
[TABLE]
[TR]
[TD="class: answercell"][/TD]
[/TR]
[/TABLE]
"Unknown protocol" error usually means, that the client and server don't agree to the SSL protocol version.

---

### Post by SeijiSensei on 2014-12-17
After reading the reply at StackOverflow, did you consider trying a different SSL protocol version?  What if you use version 2 rather than version 1 in 
```
curl_setopt($objCurl, CURLOPT_SSLVERSION, 1); 
```

---

### Post by ofnuts on 2014-12-17
Could it be a problem of certicate not available on the 14.04 server?

---

