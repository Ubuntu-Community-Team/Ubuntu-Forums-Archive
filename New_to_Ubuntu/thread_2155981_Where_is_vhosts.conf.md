---
title: "Where is vhosts.conf ?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by kamrava on 2013-06-20
Hi

I have installed `lamp-server` successfully.

I need to edit `vhosts.conf`. I can't find it ! 

Where is it ?

Thank You

---

### Post by dino99 on 2013-06-20
The virtual hosts conf by defualt is disabled in httpd.conf, in order to allow virtual hosts
in XAMPP under Ubuntu you have to uncomment line 480 in httpd.conf:

MAINSTEP: Uncomment line 480 as below:

479. # Virtual hosts
480. Include etc/extra/httpd-vhosts.conf
The httpd.conf file is located under /opt/lampp/etc, to modify it just follow these steps:

1. run sudo gedit /opt/lampp/etc/httpd.conf
2. apply MAINSTEP

[http://stackoverflow.com/questions/10878284/virtual-hosts-xampp-linux-ubuntu-not-working](http://stackoverflow.com/questions/10878284/virtual-hosts-xampp-linux-ubuntu-not-working)

---

