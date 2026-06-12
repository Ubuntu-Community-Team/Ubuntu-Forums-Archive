---
title: "what's libmysql-java"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by bayarja on 2008-05-08
hi all. i can connect java with mysql xp. but i couldn't connect java with mysql in ubuntu. so what's that libmysql-java, how to use it?

---

### Post by amohanty on 2008-05-09
> $ apt-cache search --names-only libmysql-java
libmysql-java - Java database (JDBC) driver for MySQL

They are the JDBC drivers for mysql. On XP it is likely that the mysql installer comes with the JDBC drivers as part of the installer. Once you install these, you can use them the same way you used them on windows:

1. import the JDBC connector packages
2. write the code to connect to MySQL

HTH
AM

---

### Post by ahvargas on 2008-05-09
You can try to install wajig:

apt-get install wajig

Wajig is a single commandline wrapper around apt, apt-cache, dpkg,
 /etc/init.d scripts and more, intended to be easy to use and providing
 extensive documentation for all of its functions.
 .
 With a suitable sudo(1) configuration, most (if not all) package installation
 as well as creation tasks can be done from a user shell. Wajig is also
 suitable for general system administration.
 .
 A Gnome GUI command 'gjig' is also included in the package.

then :

wajig detail libmysql-java

---

