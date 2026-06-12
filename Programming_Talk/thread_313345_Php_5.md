---
title: "Php 5"
date: 2006-12-05
forum: Programming Talk
---

### Post by rozilla on 2006-12-05
what do i have to do to be able to write php scripts and test them locally on my ubuntu desktop?
basically, i want to learn php.

---

### Post by scxtt on 2006-12-05
install php5: sudo aptitude install php5
install apache2: sudo aptitude install apache2

then create some scripts, make sure apache is running and navigate to [http://localhost/path/to/file.php](http://localhost/path/to/file.php)

---

### Post by invalid on 2006-12-05
> **rozilla said:**
> what do i have to do to be able to write php scripts and test them locally on my ubuntu desktop?
basically, i want to learn php.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

(Skip the MySQL bits if you don't want it)

---

### Post by adamkane on 2006-12-05
Why are you learning PHP? The main reason to learn PHP is to use Linux + Apache + MySQL + PHP = LAMP, so you probably want to install LAMP, not just PHP.

---

### Post by tocleora on 2006-12-06
> **adamkane said:**
> Why are you learning PHP? The main reason to learn PHP is to use Linux + Apache + MySQL + PHP = LAMP, so you probably want to install LAMP, not just PHP.

I'm guessing by this statement "what do i have to do to be able to write php scripts", he's new and wasn't aware.  

You *can* just install PHP, I have a few PHP scripts I run from the console like this:

php /folder/to/file.php

But Apache will "serve" the php file as a web page so you'll want that if you want to do web stuff.

MySQL is database so unless you are wanting to do that it's not required either.

You've taken care of the "L" by using Ubuntu. :)  For the record, you *can* install Apache, PHP and MySQL in Windows, I have it running on my Windows Partition.  But I'm not suggesting that by any means! :D

---

### Post by Verminox on 2006-12-06
For home web development and testing, get [XAMPP for Linux](www.apachefriends.org/lampp-en.html) (a.k.a LAMPP). It will also install other commonly used stufflike phpmyadmin, extra php libraries, perl, SQLlite, etc.

I have it installed on both Windows and Linux. It's ideal if you want to just develop locally and test stuff.

Install all the different software manually and configure bit-by-bit if you actually want to start a publicly accessible web server, which I doubt you want to do.

---

