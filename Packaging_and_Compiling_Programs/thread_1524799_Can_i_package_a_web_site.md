---
title: "Can i package a web site ???"
date: 2010-07-05
forum: Packaging and Compiling Programs
---

### Post by tuthmosis on 2010-07-05
I created a web application and need to build a package so that it can be deployed easily by my clients.

The web application (everything goes into /var/www)
1) Server side PHP, MySQL
2) Client side in Flex
3) SQL scripts need to be executed

Dependencies:
1) sudo
2) mdadm
3) many many other stuff usually installed manually with apt-get

I guess someone made a GUI application to easilly create .deb or .rm packages ?

Thanks !

---

### Post by Umang on 2010-07-06
You can try emailing [email]debian-webapps@lists.debian.org[/email] for help and read their policy also. Specific Debian Policies generally have some information on how to do things as well as their own rules.

Here's their draft policy: [http://webapps-common.alioth.debian.org/draft/html/](http://webapps-common.alioth.debian.org/draft/html/)

Specifically, there's a mention on NOT putting things into /var/www/, etc. [http://webapps-common.alioth.debian.org/draft/html/ch-issues.html#s-issues-fhs](http://webapps-common.alioth.debian.org/draft/html/ch-issues.html#s-issues-fhs)

---

