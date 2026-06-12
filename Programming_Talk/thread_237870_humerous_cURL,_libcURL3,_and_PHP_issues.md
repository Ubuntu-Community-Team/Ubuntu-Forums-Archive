---
title: "humerous cURL, libcURL3, and PHP issues"
date: 2006-08-16
forum: Programming Talk
---

### Post by afbase on 2006-08-16
ok I want to install the php5-curl mod onto my dapper server.  This is begginging to be very troublesome. I have already done the following:
```
apt-get install curl
apt-get install libcurl3
apt-get install php5-curl
```

Ya sure curl works stand alone but when I try to run my little php script below, i receive a frustrating error "Fatal error: Unknown function: curl_init() in C:\xamp\xampp\htdocs\price.php on line 3"

NOTE: This error is coming from my ubuntu LINUX server. (yes, you can laugh at the error if it helps)

I wrote my following on my msft xp computer, saved it as C:\xamp\xampp\htdocs\price.php then I putty/wget the file to my server.

 ```

<?php
$url = "http://moneycentral.msn.com/detail/stock_quote";
$ch = curl_init();    
curl_setopt($ch, CURLOPT_URL,$url);
curl_setopt($ch, CURLOPT_FAILONERROR, 1);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,1); 
curl_setopt($ch, CURLOPT_TIMEOUT, 3); 
curl_setopt($ch, CURLOPT_POST, 1); 
curl_setopt($ch, CURLOPT_POSTFIELDS, "Symbol=".$_GET['ticker'].""); // add POST fields
$result = curl_exec($ch); // run the whole process
curl_close($ch); 
echo $result; 


?>
```

eh anybody got any ideas???

---

### Post by az_human on 2006-08-16
Is the curl extension being called to load in your PHP.INI file?

---

### Post by afbase on 2006-08-16
i do believe so. I inserted into my php.ini file:
extension=libcurl.so

---

### Post by az_human on 2006-08-17
Try:

extension=curl.so

---

### Post by LordHunter317 on 2006-08-17
And make sure you edited the right php.ini, as their are several of them on your system most-likely.

---

### Post by BreddS on 2006-08-18
"I'm looking for PHP that would Query my user interactive pages and list those changes in my news page for when other users enter they see what has been added in different areas of the website to onclude picture databases. It would be set for say the newst changes and additions by users sum of 15 and include last changes by users sum of 15.

Example: user Tom uploaded a picture with description of his motorcycle in my picture database, and user Julie added a news article in my in my submit news area and so on...

How do I do this?"

---

### Post by adam_pretty on 2007-04-27
EDIT: Realised I switched back to php4 so needed the php4-curl package..... doh!

I'm also having problems with cUrl now...

installed all the packages, curl works from terminal.. added extension=curl.so to the current php.ini file (and all others I could find!) - restarted apache, ubuntu a few times but no joy, nothing shows up in phpinfo. Any ideas?

Do I need to recompile php??

Thanks
Adam.

---

### Post by giacomolg on 2007-06-07
Same issue here, tried extension= curl.so and libcurl.so. Is it normal that apache doesn't fire any error at (re)start no matter what module I tell it to load?

---

