---
title: "Stuck in XAMPP Hell"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by Rebootin on 2013-05-21
I am running Ubuntu 12.04. I am new to Ubuntu and I am trying to set up LAMPP. I downloaded and installed XAMPP for Linux. I could browse to localhost and got the text screen “It works”. I think I should have seen the XAMPP graphics screen. I also found out  I already had mysql-server 5.5.31. So XAMPP had a problem installing sql-server.
 

 I uninstalled the mysql-server 5.5.31using Ubuntu Software Center and started researching where to install a new sql-server that XAMPP could use. This is when I realized I was screwed!
 

 Upon browsing my file system, I found the XAMPP installed path at /opt/lampp. This path included /var/mysql, /var/perl, /var/proftpd, /var/run. I also found the path /etc/apache2 and /run/apache2 (which was empty) and /run/mysqld (which only had 2 files in it). And I also found /var/www (which had the index.html that localhost loaded).
 

 I am a little lost... I can stop XAMPP and when I start it again I get the text:
 Starting XAMPP for Linux 1.8.1... 
 XAMPP: Another web server daemon is already running. 
 XAMPP: Another MySQL daemon is already running. 
 XAMPP: Starting ProFTPD... 
 XAMPP for Linux started.
 

 How do I clean this up? My goal is to install Joomla! and develop my website on my local machine instead of doing my developing on the host server.
 

 Thanx
 Michael

---

### Post by lykwydchykyn on 2013-05-21
IMHO the first mistake is installing XAMPP.  I understand why this is popular on Windows, but Ubuntu and most other Linux distros provide a very solid, easy to install LAMP stack via the package manager.

I suggest you remove XAMPP, and check out this page for instructions on installing a native LAMP stack:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Rebootin on 2013-05-28
I agree. Thanks for stateing the obvious. I am dumping XAMPP. ;)

---

