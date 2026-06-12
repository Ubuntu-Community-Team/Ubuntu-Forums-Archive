---
title: "php error call to undefined function imagecreatefromjpeg()"
date: 2015-07-22
forum: Programming Talk
---

### Post by tross2 on 2015-07-22
I'm getting " call to undefined function imagecreatefromjpeg() " when I run my PHP script on my upload image web page.

I have php 5.5.9 installed but phpinfo() does not show any GD info.
I have installed/reinstall php5-gd, but it says that it's already installed.
when I run php -I , it echos GD in red, nothing else. ( one post shows that is ok, another shows more info)
when I run php -m , it shows the GD mod in the list
I tried the extension_dir options listed in some posts (remove the ; in front -- ext_dir =./, etc), the php -m shows that it could not find the gd.so and a few other mods( so I undid this and php.ini is back to default/normal).

is the install incomplete or is something missing?

the web site is in var/www  with root:www-data 
permissions are either 770 or 777 ( using 777 on the php script and the upload target direct -- till I fixes this then hope to have 770 on all www subdirectories.)

TIA Tim

---

### Post by tross2 on 2015-07-23
restarting the apache server as recommended in some of the posts, did not fix the problem, it required a reboot of the server.
I no longer get the error , looks like something else needs to be loaded or restarted after installing the php5-gd package.

php-info() now shows a GD section.

---

