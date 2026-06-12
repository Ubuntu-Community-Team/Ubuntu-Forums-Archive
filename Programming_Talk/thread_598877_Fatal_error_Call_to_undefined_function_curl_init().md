---
title: "Fatal error: Call to undefined function curl_init()"
date: 2007-10-31
forum: Programming Talk
---

### Post by McHenry on 2007-10-31
I have encountered a problem with a script that runs from the command line which has run perfectly until now. I have created a small test script to pinpoint the problem but am now stuck:

admin@declan:/var/www/research$ php5 testcurl.php

Fatal error: Call to undefined function curl_init() in /var/www/research/testcurl.php on line 3
admin@declan:/var/www/research$ 

The script was copied from:
[http://au2.php.net/curl_init](http://au2.php.net/curl_init)

I have checked phpinfo and curl is enabled.

Any ideas would be greatly appreciated.

Edit:
When I run testcurl.php from the browser it appears to work but not from the command line. So what I am suspecting is that phpcli is not working witrh curl etc whereas php is. Maybe a recent upg or similar has removed the curl extension from the php.ini file that is used by the cli, however I do not know where this ini file is located...

Thanks

---

### Post by dataw0lf on 2007-10-31
Most likely, you have two versions of PHP installed (one without cURL support).  Are you using XAMPP?

---

### Post by McHenry on 2007-10-31
Just a basic dapper server.

admin@declan:~$ sudo find /| grep php.ini
/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini
/usr/share/doc/php5-common/examples/php.ini-recommended
/usr/share/doc/php5-common/examples/php.ini-paranoid
/usr/share/doc/php5-common/examples/php.ini-dist
/usr/share/php5/php.ini-dist
admin@declan:~$ 

admin@declan:~$ sudo cat /etc/php5/apache2/php.ini | grep curl
extension=curl.so
admin@declan:~$ 

admin@declan:~$ sudo cat /etc/php5/cli/php.ini | grep curl
extension=curl.so
admin@declan:~$ 

admin@declan:~$ php -v
PHP 5.1.2 (cli) (built: Jul 17 2007 17:32:48)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies

admin@declan:~$ php5 -v
PHP 5.1.2 (cli) (built: Jul 17 2007 17:32:48)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies
admin@declan:~$

---

### Post by dataw0lf on 2007-10-31
Huh.  Are you sure php5-curl is installed?

Also, regarding :
> sudo find /| grep php.ini

It'd be better to write that as:
```
sudo find / -name "php.ini" -type f 
```

---

### Post by McHenry on 2007-10-31
admin@declan:/var/www/research$ php phpinfo.php | grep php.ini
Configuration File (php.ini) Path => /etc/php5/cli
admin@declan:/var/www/research$ 

admin@declan:/var/www/research$ php phpinfo.php | grep curl
admin@declan:/var/www/research$ 


So it appears in the ini file that curl.so is enabled however the cli phpinfo shows no sign of curl being enabled.

---

### Post by McHenry on 2007-10-31
[QUOTE=dataw0lf;3680602]Huh.  Are you sure php5-curl is installed?

The browser version of phpinfo.php displays the following so it must be... ?

curl
CURL support 	enabled
CURL Information 	libcurl/7.15.1 OpenSSL/0.9.8a zlib/1.2.3 libidn/0.5.18



admin@declan:/var/www/research$  sudo apt-get install php5-curl
Reading package lists... Done
Building dependency tree... Done
php5-curl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
admin@declan:/var/www/research$

---

### Post by McHenry on 2007-11-01
I have also notice that the mysql extension is not being loaded either.

So the question is why would the mysql and curl extensions not be loaded even though they are in the ini file to be loaded ?

---

### Post by smartbei on 2007-11-01
I'm not at my ubuntu desktop ATM but If I remember correctly there is a seperate ini for the CLI version. Try looking in /etc/php or /etc/php5, sorry - can't remember which. I was using curl from the command line in php as well.

---

### Post by McHenry on 2007-11-01
Yes, thanks. I have identified the two ini files in the posts above and have checked both have the modules enabled.

---

### Post by dataw0lf on 2007-11-01
Try explicitly specifying the ini the CLI uses on the command line, with a copy of the CLI php.ini.

---

### Post by zazuge on 2008-05-12
sudo apt-get install php5-curl

---

### Post by adam_89 on 2008-06-29
for,me after restarting the server application (apache2 -k restart),it worked

---

### Post by benipsen on 2009-12-04
Just posting this tip for anyone that came across this forum post having the same problem as I did. 

On my Hardy install on the Rackspace Cloud I had to change my extension_dir from './' to './conf.d/'

Hope that helps someone else out! 

Ben

---

