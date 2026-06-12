---
title: "Php cURL convert to bash need help"
date: 2009-02-18
forum: Programming Talk
---

### Post by aliahsan81 on 2009-02-18
I have google it but didnt find much material regading Curl in bash script.

I have php script that contain Curl.I need to convert to bash to use in my script i dont  Curl much this is a helper script that i want to use in my script.So it will be very nice if some on convert this Curl php scipt to bash script 

```



<?php

$ch = curl_init();
$res= curl_setopt ($ch, CURLOPT_URL,"MYURL");

curl_setopt ($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
curl_setopt ($ch, CURLOPT_HEADER, 0);
curl_setopt ($ch, CURLOPT_HTTPAUTH,CURLAUTH_BASIC);
curl_setopt ($ch, CURLOPT_USERPWD,"uname:password" );
curl_setopt ($ch, CURLOPT_CRLF,TRUE);
curl_setopt ($ch, CURLOPT_RETURNTRANSFER,true);
$data = curl_exec ($ch);
curl_close ($ch);



echo $data  ;


?>


```

---

### Post by ghostdog74 on 2009-02-18
you can download curl as a package and compile on your platform. Or just search for its binary in google.

---

