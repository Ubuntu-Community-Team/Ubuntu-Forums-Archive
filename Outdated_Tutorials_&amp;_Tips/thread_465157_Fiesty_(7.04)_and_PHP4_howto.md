---
title: "Fiesty (7.04) and PHP4 howto"
date: 2007-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by pestilence on 2007-06-05
Ok since I see allot of users asking how to enable PHP4 support into feisty - after its removal from the development team - This is the method I followed to have PHP4 enabled into feisty hassle and compile free.
Initially I thought of compiling the package (php) but then again I wanted to have a sollied and nice php package installed into the system, compatible with adept and everything.
What was the easiest solution to follow? Install Debian packages, since Debian has not removed yet support for PHP4.

[B]1)  libapache2-mod-php4_4.4.4-9+lenny1_i386.deb
php4_4.4.4-9+lenny1_all.deb
php4-cli_4.4.4-9+lenny1_i386.deb
php4-common_4.4.4-9+lenny1_i386.deb
php4-curl_4.4.4-9+lenny1_i386.deb
php4-gd_4.4.4-9+lenny1_i386.deb
php4-mysql_4.4.4-9+lenny1_i386.deb[/B]


From a Debian repository (e.g: [ftp://ftp.somedebianmirror.com/pub/linux/debian/pool/main/p/php4/](ftp://ftp.somedebianmirror.com/pub/linux/debian/pool/main/p/php4/))

[B]2) Install through adept:
libzzip-0-12
apache2
apache2.2-common
apache2-mpm-prefork[/B]

After Installing the apache files proceed installing the php packages downloaded in step1. Reload your server and you should have php4 support!

---

