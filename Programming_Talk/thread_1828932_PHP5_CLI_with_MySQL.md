---
title: "PHP5 CLI with MySQL"
date: 2011-08-19
forum: Programming Talk
---

### Post by Sarteck on 2011-08-19
I'm trying to create a PHP script to grab some information from my database and create a file with that information.

I can get the Script to execute, but it seems that it fails to load the MySQL extensions.

**php5-mysql** is installed.

**/etc/php5/cli/php.ini** has **extension=mysql.so** in it.

**php5 -i | grep mysql** does *NOT* return anything.  :(

Running my script gives me the error:
**Fatal error: Call to undefined function mysql_connect() in /home/sarteck/pisg_conf.php on line 11**



Could someone maybe give me some pointers on where I may be going wrong, here?

---

### Post by Sarteck on 2011-08-19
I feel like a retard....

**extension=mysql.so** was actually **extension-mysql.so** in my ini file.

/me facepalms

After correcting that, things are running as expected.

---

### Post by Habitual on 2011-08-21
+1 for fixing it yourself. :)

---

