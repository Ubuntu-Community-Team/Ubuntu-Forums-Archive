---
title: "How is image magick running?"
date: 2019-05-22
forum: Programming Talk
---

### Post by dwhitifled on 2019-05-22
I am not sure this is the proper sub-forum, but it deals with php.ini, so I thought maybe it should go here due to PHP.

Three times now our PHP application has had multiple apache2  threads that have gone to high CPU (one thread taking between 50-90% of a  CPU) and high memory (several threads in 30-40% of memory) usage.   We've also noticed that the imagick directory  is getting several gigabytes of files created during this high  CPU/memory time. 

While the instance was in progress, I looked for `imag` in the process list, and was unable to locate any processes with that name.

I can only assume that ImageMagick is being launched by the apache2 threads, but when I looked at both of the php.ini files on the system, there are no extensions being load at all, including ImageMagick.

I would have anticipated the PHP Apache module's php.ini would have had the the following line:
extension=imagick.so

Might there be another way ImageMagick is being called?

```

php -v
PHP 5.6.26-0+deb8u1 (cli) (built: Sep 21 2016 12:37:50)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2016, by Zend
Technologies
```


Yes, I know PHP 5.6 is EOLed. I can't do anything about that (unless, MAYBE, if someone can point me to something that would directly cause this).

```
apt-cache policy imagemagick-common

imagemagick-common:
Installed: 8:6.8.9.9-5+deb8u5
Candidate: 8:6.8.9.9-5+deb8u16
Version table: 8:6.8.9.9-5+deb8u16 0
```

---

### Post by TheFu on 2019-05-22
The program names aren't "ImageMagick" ... they are "convert" or "import" or ...  if you check the ImageMagick manpage, there should be a list.  Oddly, I don't have that manpage installed, but I do have the **convert** manpage.  

I don't know anything about php. Might there be a php interface to the ImageMagick library?

---

### Post by norobro on 2019-05-22
> **dwhitifled said:**
> Might there be another way ImageMagick is being called?
Only have access to Debian at the moment. I assume it is the same for Ubuntu:```
$ ls -l /etc/php/7.3/apache2/conf.d/*imagick*
lrwxrwxrwx 1 root root 39 May 22 16:49 /etc/php/7.3/apache2/conf.d/20-imagick.ini -> /etc/php/7.3/mods-available/imagick.ini


$ cat /etc/php/7.3/apache2/conf.d/*imagick*      
; configuration for php imagick module
extension=imagick.so

```

---

### Post by SeijiSensei on 2019-05-23
Maybe there's an exec() or shell_exec() function call that invokes convert?

Have you grepped all the PHP files for "convert"?

Create a file called "info.php" in the root of your website like this:

```

cd /var/www/html
echo '<?php phpinfo() ?>' > info.php

```

Then invoke it with a browser.  You'll see a complete census of everything PHP is using and the modules installed.

---

### Post by dwhitifled on 2019-05-23
> **norobro said:**
> Only have access to Debian at the moment.

I'm actually on Debian in this particular case. You can see I'm using the Debian package in my apt output.

I figured it was close enough though.

Thanks for the thoughts!

---

### Post by norobro on 2019-05-23
You're welcome. 

If you uninstall that module (or rename it) your apache error log should show you where in your app imagemagick is being called. 

On my local machine I renamed the imagick.ini to imagick.ini.bak and ran example #3 from here: [https://www.php.net/manual/en/imagick.examples-1.php](https://www.php.net/manual/en/imagick.examples-1.php)

Here's the relevant error log entry:```
[Wed May 22 20:56:07.881762 2019] [php7:error] [pid 23328] [client 192.168.2.3:35660] PHP Fatal error:  Uncaught Error: Class 'Imagick' not found in /var/www/php_test/imagemagick/ex_3.php:3\nStack trace:\n#0 {main}\n  thrown in /var/www/php_test/imagemagick/ex_3.php on line 3, referer: [http://192.168.2.3/php_test/imagemagick/](http://192.168.2.3/php_test/imagemagick/)
```

---

