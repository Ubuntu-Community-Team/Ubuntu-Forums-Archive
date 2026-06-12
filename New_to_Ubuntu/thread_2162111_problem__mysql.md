---
title: "problem  mysql"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by hussiniraq on 2013-07-13
[SIZE=4]
hello ...


[PHP]
h313@h313:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
[/PHP]


The problem appear even during install phpmyadminHe thinks when entering phpmyadmin panel
Tired and I'm looking for a solution [/SIZE]:([SIZE=4][/SIZE]:([SIZE=4]

[IMG]http://im36.gulfup.com/rmQVU.png[/IMG]
[/SIZE]

---

### Post by dannyboy79 on 2013-07-13
did you forget the password when you setup mysql? here's a guide for resetting your root mysql password
[http://www.cmdln.org/2008/02/09/reset-mysql-root-password/](http://www.cmdln.org/2008/02/09/reset-mysql-root-password/)

---

### Post by hussiniraq on 2013-07-13
also problem > h313@h313:~$ mysql -u root -pEnter password: ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)a


and images  top I'm not  forget  password

---

### Post by paulee81 on 2013-07-13
Should you use: 
[SIZE=4]sudo mysql -u root -p[/SIZE][SIZE=4][COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][/COLOR][/SIZE]

---

### Post by hussiniraq on 2013-07-13
h313@h313:~$ sudo mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by hussiniraq on 2013-07-13
/var/run/mysqld/ not found

---

### Post by steeldriver on 2013-07-13
It sounds like you don't actually have a mysql server instance running on that machine - you can check with

```

service mysql status

sudo netstat -nlp | grep mysql

dpkg -l | grep mysql

```

(the last one checks whether you have mysql-server installed)

---

### Post by The Cog on 2013-07-13
"Access denied for user 'root'@'localhost' (using password: YES)" will not happen unless he connects to the mysql daemon. If it's not running you get  "Can't connect to local MySQL server".

My guess is that you have the wrong password. 
This is a way to reset the password.
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

If you are sure you have it right, then perhaps you should consider that it might have been guessed and changed by someone else.

---

### Post by hussiniraq on 2013-07-13
> h313@h313:~$ service mysql status
mysql stop/waiting





> h313@h313:~$ sudo netstat -nlp | grep mysql
[sudo] password for h313: 
h313@h313:~$ dpkg -l | grep mysql
ii  libdbd-mysql-perl                               4.020-1build2                           Perl5 database interface to the MySQL database
ii  libmysqlclient18                                5.5.31-0ubuntu0.12.04.2                 MySQL database client library
ii  libmysqlclient18:i386                           5.5.31-0ubuntu0.12.04.2                 MySQL database client library
ii  libqt4-sql-mysql                                4:4.8.1-0ubuntu4.4                      Qt 4 MySQL database driver
ii  libqt4-sql-mysql:i386                           4:4.8.1-0ubuntu4.4                      Qt 4 MySQL database driver
ii  mysql-client                                    5.5.31-0ubuntu0.12.04.2                 MySQL database client (metapackage depending on the latest version)
ii  mysql-client-5.5                                5.5.31-0ubuntu0.12.04.2                 MySQL database client binaries
ii  mysql-client-core-5.5                           5.5.31-0ubuntu0.12.04.2                 MySQL database core client binaries
ii  mysql-common                                    5.5.31-0ubuntu0.12.04.2                 MySQL database common files, e.g. /etc/mysql/my.cnf
ii  mysql-server                                    5.5.31-0ubuntu0.12.04.2                 MySQL database server (metapackage depending on the latest version)
ii  mysql-server-5.5                                5.5.31-0ubuntu0.12.04.2                 MySQL database server binaries and system database setup
ii  mysql-server-core-5.5                           5.5.31-0ubuntu0.12.04.2                 MySQL database server binaries
ii  php5-mysql                                      5.3.10-1ubuntu3.6                       MySQL module for php5
h313@h313:~$ 



top :(

---

### Post by steeldriver on 2013-07-13
Try starting it - post back if you get errors

```
sudo service mysql start
```

---

### Post by hussiniraq on 2013-07-15
root@h313:/var/run/mysqld# sudo service mysql start
start: Job failed to start

---

### Post by dannyboy79 on 2013-07-15
is there anything within /var/log/ related to mysql so we can see why it's not starting?

---

