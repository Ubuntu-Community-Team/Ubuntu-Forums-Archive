---
title: "XAMPP won't connect."
date: 2009-01-17
forum: Programming Talk
---

### Post by hoboy on 2009-01-17
I have installed xampp it start very well I can connect to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) 
I have installed Mysql Administrator and Msql querry Browser using synactic
but I can not connect to the mysql db true Administrator or querry Browser.
On the console I am getting the following error
when I use mysql
I get the following error
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
After long time googling here I am

---

### Post by Dr Small on 2009-01-17
XAMPP comes with MySQL, so installing MySQL from the repositories is causing a daemon conflict.

---

