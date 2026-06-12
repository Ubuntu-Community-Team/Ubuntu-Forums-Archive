---
title: "php &amp; mysql"
date: 2011-03-09
forum: Programming Talk
---

### Post by rahulbest on 2011-03-09
i m new to ubuntu and programming....i m trying out php and mysql.
i run simple php pages...it get executed...but when i run with mysql it shows blank screen...
i want to know whether mysql is been installed in my system or not?

---

### Post by Habitual on 2011-03-09
```
mysql -uroot -p 
```

will tell you if mysql is  installed properly and is listening.

```
telnet localhost 3306
```
will tell you if mysql is listening.

```
pidof mysql
``` or ```
pidof mysqld
```
will tell you if mysql is listening.

Have a look at [https://help.ubuntu.com/10.04/serverguide/C/mysql.html](https://help.ubuntu.com/10.04/serverguide/C/mysql.html)

and let us know...

---

### Post by pqwoerituytrueiwoq on 2011-03-09
check the http headers you are probably getting a 500 error cause of a missing semi-colon in your script (or you forget to select a database in mysql or something)
enable error reporting in php.ini
/etc/php5/apache2/php.ini
i think it is on line 514

---

### Post by s.fox on 2011-03-09
Thread moved to  [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

