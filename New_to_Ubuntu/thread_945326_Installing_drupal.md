---
title: "Installing drupal"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Newbie95 on 2008-10-12
Hi everyone.

I am having trouble installing latest version of drupal 6.4
I have installed all the lamp packages : apache2 php5-mysql php5-gd libapache2-mod-php5 mysql-server
When I want to install drupal [http://localhost/drupal](http://localhost/drupal)
I get stuck on Step 3 setting up database.
I need to create drupal database name, username and password in mysql
but mysql won't open  *mysql -u root*
then I get this error: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I am still very new to ubuntu & mysql
So any help would be great, thanx!!

---

### Post by leg on 2008-10-12
Probably because you have to use a password. Create a different user (in mysql) that has a username and a password and give that user permissions over the database you have created for Drupal.

---

