---
title: "Setting up MySql, Ubuntu 13.10"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by Rebecca_D on 2014-01-25
It maybe that this is not the place to ask this question for which I apologise, but if there is any help you can give me I would be very obliged.

I have recently installed PHP, MySQL, Apache Server and phpMyAdmin on my Ubutu 13.10 PC. I am used to using these to build and maintain websites and associated databases along with cPanel on web servers, but have decided that it would be useful to be able to build and test php pages/MySQL databases locally.

The installation of the above went smothly and Apache amd phpMyadmin are working correctly. My document root folder is /var/www which I have chmod to 777. I have copied some files that I also have on a website and exported its associated database and imported it locally through phpMyadmin.

The php files render correctly in my browser but I do not seem to be able to link to the database. The connection is controlled by a config file which lists hostname, database name, database user and database password. I am used to setting up databases online through cpanel which gives you all of these parameters.

My question is, when setting up databases locally are the database user and database password the same as the user name and password for phpMyAdmin, which for me would be root and <an undiclosed password> ? I don't know of ways of setting up users and associated passwords as you would do through cPanel. Will these values be the same for all databases created or do/can seperate users be created?

Many thanks.

---

### Post by galvatron408 on 2014-01-26
> **Rebecca_D said:**
> 
My question is, when setting up databases locally are the database user and database password the same as the user name and password for phpMyAdmin, which for me would be root and <an undiclosed password> ? I don't know of ways of setting up users and associated passwords as you would do through cPanel. Will these values be the same for all databases created or do/can seperate users be created?

Many thanks.

You got it reversed. PhpMyAdmin uses the DB User name and password.

---

