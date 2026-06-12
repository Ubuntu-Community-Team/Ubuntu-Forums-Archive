---
title: "Ubuntu 12.04 mysql.log says I can' t connect through socket"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by elvijs2 on 2013-10-11
Hello. Encountered a problem with MySQL, hope you can help.
Running Ubuntu 12.04 32bit on virtual machine (VMware). Installed MySQL server and it seems to be working. Checked server status with #sudo service mysql status and it showed "mysql start/running, process 7969". Used #mysqladmin -u root -p status to check status and got "Uptime: 64 Threads: 1 Questions: 104....etc.". Started mysql client with #mysql -u root -p and created a database with a table, everything worked ok.
But when I do #sudo cat /var/log/upstart/mysql.log I get errors about sockets. Here' s what it says:
```
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
mysqld is alive
Checking for tables which need an upgrade, are corrupt or were not closed cleanly.

```
I checked that directory and when server is up, it contains files mysqld.pid and mysqld.sock. Restarted the server, reinstalled MySQL, but that didn' t help.
As I' m new both to Ubuntu and MySQL, I don' t know what more info you need, so ask, if you need anything.

---

### Post by L486XGW on 2013-10-11
Check the /etc/mysql/my.cnf file to make sure you have the right socket file setup in the sections. [COLOR=#000000][FONT=Ubuntu Mono]/var/run/mysqld/mysqld.sock probably doesnt exist[/FONT][/COLOR]

---

### Post by elvijs2 on 2013-10-11
My my.cnf file is the default version, since I reinstalled the whole thing. Paths seem to be correct.  [ATTACH]246876[/ATTACH]

---

