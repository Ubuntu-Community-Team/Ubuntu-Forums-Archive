---
title: "Questions about setting up LAMP"
date: 2008-12-18
forum: Programming Talk
---

### Post by aqwabawks on 2008-12-18
Recently I installed a copy of Ubuntu Linux (8.04) with the intention of setting up a web development environment so I can learn MySQL, PHP, Python and Ruby/Rails.

I was following this guide to setup it all up: [http://maff.ailoo.net/2008/07/quick-and-dirty-set-up-a-local-php-and-ruby-development-environment-on-ubuntu-hardy-heron-804/](http://maff.ailoo.net/2008/07/quick-and-dirty-set-up-a-local-php-and-ruby-development-environment-on-ubuntu-hardy-heron-804/)

Now I can access the pma, localhost, and railsproject locations in Firefox on my Ubuntu desktop, however, when I try to access it from another PC on my network all I can get is the localhost (by using the Ubuntu PC's IP address). I was wondering how I could get at the railsproject and pma folders (I can access phpmyadmin via the ip/phpmyaddress) from this other PC.

Pretty much what I want to be able to do is do my programming on a different PC and be able to upload my files to my Ubuntu PC for testing and such.  Also is it at all possible to setup MySQL so I can create databases and tables via the terminal rather than a web-based solution such as PhpMyAdmin?

---

### Post by .Maleficus. on 2008-12-19
I don't know about accessing the other sites part, but as for MySQL, all you would need to do is SSH to your Ubuntu box (on Windows PuTTY is a great program) and run the 'mysql' command.
```
$mysql -u root -p
<MySQL will ask for your MySQL root account's password>
mysql> CREATE DATABASE data_base;
mysql> USE data_base;
```
That will get you a database with no tables.  As for the rest of it, you'll need to learn proper SQL syntax.

---

