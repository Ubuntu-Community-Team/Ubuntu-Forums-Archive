---
title: "[SOLVED] Wireless connection broken after LAMP install"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by UltimateNewbie on 2008-11-27
Hi,

I just installed Ubuntu for the first time, the reason is I want to learn PHP and MySQL to make groovie sites.  :)

But, after installing Apache, PHP, MySQL and phpMyAdmin using this guide:
[http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/)

I lost my wireless connection. Well, not straight away. Used some time to figure out how to make the file *fqdn *with content “*ServerName localhost*” into [I]/etc/apache2/conf.d
[/I]
It seems to me that connection got broken after adding fqdn file and rebooting. Anyone had the same trouble or know the solution, I'd be most grateful!

Thanks

---

### Post by UltimateNewbie on 2008-11-27
Feel like updating the post a little:

The installation of Apache, PHP, mySQL and phpMyAdmin happened right after installing Ubuntu 8.10.
The internet connection worked fine also after this except phpMyAdmin did not work because I couldn't work out how to create the file *fqdn*. But wireless connection worked fine. I turned of the laptop.
Next day, I turned on the laptop, wireless works like a charm. And i scope the net and figure out that I can use 

*sudo su* 

in terminal to "be" root. 
From there i manage to create the file using

[I]gksu gedit /etc/apache2/conf.d/fqdn

tested that it worked to type [/I][http://localhost/randomfile.php](http://localhost/randomfile.php) [I]and turned of the machine. 
Next time i turned it back on.... BAM!! ..... connection gone. :P

Just keeps asking me for a WPA WPA2 passkey. The one Ive typed a hundred times is the right one, but keeps aksing me for the key as if the one I typed was wrong.

Help... Anybody... Hello... :P

Thanks
[/I]

---

### Post by UltimateNewbie on 2008-11-28
bump

---

### Post by UltimateNewbie on 2008-11-29
Sorry for this one. Turned out it was fault by router.

---

