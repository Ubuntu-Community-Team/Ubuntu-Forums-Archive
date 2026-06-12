---
title: "Setting up development environment for Apache 2, PHP 5 and MySQL 5 in Gutsy"
date: 2007-10-31
forum: Programming Talk
---

### Post by tc101 on 2007-10-31
I just installed Gutsy and everything went fine.  I want to start learning PHP so I need to install Apache 2, PHP 5 and MySQL 5.  I found this guide and it seems pretty simple:

[http://services.tucows.com/developers/2007/10/24/installing-apache-2-php-5-and-mysql-5-on-ubuntu-710-aka-gutsy-gibbon/](http://services.tucows.com/developers/2007/10/24/installing-apache-2-php-5-and-mysql-5-on-ubuntu-710-aka-gutsy-gibbon/)

But I have found other messages saying people are having problems with apache and gutsy.  

Several questions:

1.  Do you think I should wait a week to let any compatability issues between apache and gutsy get fixed.

2.  I have mySQL already installed.  I don't remember the version though.  How do I find the version of what is currently on my computer?

---

### Post by dataw0lf on 2007-10-31
I'm not using Gutsy, so I can't give you any advice.  That question would probably be more applicable in the Servers subforum, anyways.

To get the mysql version, just type mysql -V at a bash prompt.

Cheers!

---

### Post by oooooops on 2007-11-01
> **tc101 said:**
> I just installed Gutsy and everything went fine.  I want to start learning PHP so I need to install Apache 2, PHP 5 and MySQL 5.  I found this guide and it seems pretty simple:



If your sole purpose is to start learning and using solely as a development environment I suggest xampp [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

I don't know if there is a package for it but it's very simple to untar and run (even from your home directoy).  The only issue you might have would be the fact that you already have mysql installed.

xampp also has ties to the PDT for Eclipse for development.

---

