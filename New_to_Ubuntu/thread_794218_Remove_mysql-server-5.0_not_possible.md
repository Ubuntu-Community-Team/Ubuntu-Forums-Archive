---
title: "Remove mysql-server-5.0 not possible"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by fisfia on 2008-05-14
Hi!

I've tried to remove a package that is probably damaged or something. It does not work to remove it. The name of the package is mysql-server-5.0. If I try ```
sudo apt-get remove mysql-server-5.0
``` I got this in return: (My bad translation sorry!)

> dpkg: error when handling mysql-server-5.0 (--remove)
The package is in a inconsistent bad shape - you should try to reinstall it before you remove it.

Error in handling:
mysql-server-5.0

E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do?

---

### Post by quelx on 2008-05-14
try ```
sudo apt-get --reinstall install mysql-server
``` as the error suggests then ```
sudo apt-get remove mysql-server
```

---

### Post by fisfia on 2008-05-14
Väljer tidigare ej valt paket mysql-server-5.0.
(Läser databasen ... 143466 filer och kataloger installerade.)
Förbereder att ersätta mysql-server-5.0 5.0.51a-3ubuntu5 (med .../mysql-server-5.0_5.0.51a-3ubuntu5_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: varning - gammalt pre-removal-skript returnerade felstatus 1
dpkg - försöker skript från det nya paketet istället ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: fel vid hantering av /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5_i386.deb (--unpack):
 underprocess nytt pre-removal-skript gav felkod 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: fel vid upprensning:
 underprocess post-installation script gav felkod 1
Packar upp mysql-server (från .../mysql-server_5.0.51a-3ubuntu5_all.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: fel vid hantering av /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5_all.deb (--unpack):
 underprocess pre-installation script gav felkod 1
Fel uppstod vid hantering:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5_i386.deb
 /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dbstraffin on 2008-05-14
Looks like you just need to stop mysql server before uninstalling.  You can either stop the process manually or reboot or if that doesn't work, reboot into recovery mode.

To stop the process manually without rebooting first get the process id's:
ps -ef | grep mysql

Then kill the processes using the ids in the second column:
sudo kill -9 15691

---

### Post by fisfia on 2008-05-14
Thanx! 

I got this result from ps:

> fia@datorn:~$ ps -ef | grep mysql
root      5662     1  0 16:57 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5704  5662  0 16:57 ?        00:00:03 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5705  5662  0 16:57 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
fia      13799  9091  0 22:02 pts/0    00:00:00 grep mysql


is it 5704 on the second line? Im not sure, just guessing :confused:

---

### Post by Cypher on 2008-05-14
Try
```

sudo /etc/init.d/mysql stop

```
If that doesn't work, then try
```

sudo killall mysqld
sudo rm /var/run/mysqld/mysqld.pid
sudo rm /var/run/mysqld/mysqld.sock

```

---

### Post by fisfia on 2008-05-14
> **Cypher said:**
> Try
```

sudo /etc/init.d/mysql stop

```

Here I get [FAIL].

> If that doesn't work, then try
```

sudo killall mysqld
sudo rm /var/run/mysqld/mysqld.pid
sudo rm /var/run/mysqld/mysqld.sock

```

The first line is propably working because I get nothing in return. But the two other lines are not working. File or directory could not be removed because the file or directory does not exist.

---

### Post by ITfromScratch on 2013-04-11
I was having this same problem, and none of the solutions listed above worked. The "mysqld" process kept coming back. 

Here's the command I used to kill it for good:

```
sudo stop mysql
```

Hope that helps.

Source: [http://www.itfromscratch.com/how-to-stop-the-percona-mysql-server/](http://www.itfromscratch.com/how-to-stop-the-percona-mysql-server/)

---

### Post by wildmanne39 on 2013-04-11
Thread closed. Please do not post in old threads.

---

