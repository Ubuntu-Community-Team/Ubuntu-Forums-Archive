---
title: "PHP alexa soap script"
date: 2006-02-13
forum: Programming Talk
---

### Post by zootreeves on 2006-02-13
HI,

I'm trying to get alexa website information using their API, but I cannot figure out the authentication system. Has anyone got a script that use alexa & php?

Here is what i have got so far:

```

<?php


   	$WsdlUri = 'http://awis.amazonaws.com/AWSAlexa/AWSAlexa.wsdl';

        $params = array(
        'AWSAccessKeyId' => '<<My Access Key>>',
        'Timestamp' => time(),
        'Signature' => base64_encode("<<My Secret Key>>"),
        'Url' => "http://www.test.com";
        );
        #print time();

            $Client = new SoapClient($WsdlUri);
      	    $O =  $Client -> UrlInfo($params);

                  print_r($O);

?>

```

Which outputs:

stdClass Object ( [OperationRequest] => stdClass Object ( [HTTPHeaders] => stdClass Object ( [Header] => stdClass Object ( [Name] => UserAgent [Value] => PHP SOAP 0.1 ) ) [RequestId] => 08KVFE5SESYG5HPFDW70 [Arguments] => stdClass Object ( [Argument] => stdClass Object ( [Name] => Service [Value] => AlexaWebInfoService ) ) [Errors] => stdClass Object ( [Error] => stdClass Object ( [Code] => AWS.RequestExpired [Message] => AWS_RequestExpired_4316 ) ) ) )

---

### Post by robinharvey on 2006-07-27
WARNING!!!!!!!

php5 native soap is broken in dapper.  Check this link:

[http://ubuntuforums.org/showthread.php?t=220346](http://ubuntuforums.org/showthread.php?t=220346)

As regards your question, is the base64_encode() func necessary?  Also, check your system time, if it is out by a long way that could be preventing it working.

hth
--Robin

---

