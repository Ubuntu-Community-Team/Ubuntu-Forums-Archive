---
title: "Problem with MySQL Community Server"
date: 2018-06-24
forum: New to Ubuntu
---

### Post by hmarija on 2018-06-24
[I] I use Ubuntu 18.04 lts from yesterday (I've never used Ubuntu before) so I don't know about it.
I have a problem with installing MySQL, PHP and other things. Everything starts nicely to instill **and then this happens:**[/I]


dpkg: error processing package mysql-community-server (--configure):
 installed mysql-community-server package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-community-server (= 8.0.11-1ubuntu18.04); however:
  Package mysql-community-server is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-community-server
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

**Can somebody tell me what the problem is and how to fix it?**
**I tried to install the MySQL but also can't because of it**

---

### Post by yancek on 2018-06-24
Installing a LAMP server with apahe/mysql/php should be very simple.  What method did you use?  Give some specifics on exactly what you did to install.  Do you have a specific web site with instructions.  The below links explain it in detail.

[https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/](https://www.linode.com/docs/web-servers/lamp/install-lamp-stack-on-ubuntu-18-04/)

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04)

---

