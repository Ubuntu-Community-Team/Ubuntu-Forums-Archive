---
title: "After mysql install getting this:((("
date: 2006-04-11
forum: Repositories &amp; Backports
---

### Post by rensu on 2006-04-11
pr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested a$
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Aborting
Apr 11 21:14:16 localhost mysqld[15786]:
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 11 21:14:16 localhost mysqld[15786]:
Apr 11 21:14:16 localhost mysqld_safe[15788]: ended
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cn$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mys$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock'$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]:

What could be wrong? Just installed Ubuntu again and wanted to install lamp on my server and got this error :S

---

### Post by gerbman on 2006-04-12
[QUOTE=rensu]pr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested a$
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [ERROR] Aborting
Apr 11 21:14:16 localhost mysqld[15786]:
Apr 11 21:14:16 localhost mysqld[15786]: 060411 21:14:16 [Note] /usr/sbin/mysqld: Shutdown complete
Apr 11 21:14:16 localhost mysqld[15786]:
Apr 11 21:14:16 localhost mysqld_safe[15788]: ended
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cn$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mys$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock'$
Apr 11 21:14:22 localhost /etc/init.d/mysql[15851]:

What could be wrong? Just installed Ubuntu again and wanted to install lamp on my server and got this error :S[/QUOTE]Not sure what the problem is, but here are a few things to check. What does ```
ps -e | grep mysqld
``` output? The daemon needs to be running, first of all. Next, look in /var/run/mysqld for the file mysqld.sock. If that file isn't present you need to locate it (maybe where you installed MySQL to) and do something like ```
sudo ln -s /path/to/mysqld.sock /var/run/mysqld/mysqld.sock
```Does that get you anywhere?

---

### Post by rensu on 2006-04-12
Actually the file mysqld.sock is missing:((( After insallation it started to say that the sock fail is missing and can't start and not talking about setting a password for mysql root. It won't set because the sock file is missing I guess. And mysqld is not running because I can't start it.](*,)

---

### Post by rensu on 2006-04-13
Can somebody help me please?

---

### Post by rensu on 2006-04-13
Or if im trying to start MySQL, getting this:

Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

---

### Post by rensu on 2006-04-13
And this information too that mysql.log and mysql.err files are empty.

---

