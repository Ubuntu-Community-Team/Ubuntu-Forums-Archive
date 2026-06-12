---
title: "mysql wont start"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by 007casper on 2013-06-19
mysql was working fine.  I had to reboot the server, and mysql didnt load.  

I did /etc/init.d/mysql start
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job failed to start

```

I did mysql -u root -p
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

(2 -> No such file or directory ) comes from the fact that you have no mysql server running on localhost.


(111 -> Connection refused) shows that either mysql port is blocked (firewall for instance) or that no mysql server is running on 

```

I have been trying to figure this out for a day now without any luck.  I have tried several things that is posted online.

It just doesnt work.

please advise.  Thank you.

---

### Post by sushi80 on 2013-06-19
[COLOR=#000000]Hi 007casper

mysql -u root -p doesn't work because the service is down.
[/COLOR]
Did you try run [COLOR=#000000][FONT=Ubuntu Mono]start mysql or service mysql start ??
[/FONT][/COLOR]
check mysql log, should be in /var/log/mysql.log

---

### Post by 007casper on 2013-06-19
cd /var/log# ls
-rw-r-----  1 mysql  adm        0 2013-05-21 21:47 mysql.err
-rw-r-----  1 mysql  adm        0 2013-06-18 06:49 mysql.log

they are both empty

/var/log/mysql# ls
error.log  error.log-old

cat error.log> 
130618  3:34:57 [Warning] Disk is full writing '/tmp/#sql_84e_2.MYI' (Errcode: 28). Waiting for someone to free space... (Expect up to 60 secs delay for server to continue after freeing disk space)
130618  3:34:57 [Warning] Retry in 60 secs. Message reprinted in 600 secs
130618  3:44:57 [Warning] Disk is full writing

the disk isnt full anymore.  The problem still continues

I did autoclean
> 
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

start mysql
start: Job failed to start

service mysql start
start: Job failed to start

/var/run/mysqld/mysqld.sock didnt use to show up.

I also tried without luck
ln -s /tmp/mysql.sock /var/run/mysqld/mysql.sock

I reboot the DB server.  I have mysqld.sock now... but still no luck

partial my.cnf file
> [client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking


---

### Post by monkeybrain2012 on 2013-06-19
The command to start mysql is 

```
sudo service mysql start
```

---

### Post by 007casper on 2013-06-19
changed mysql

cd /var/lib# ls -al
drwxrw----  5 mysql   root    4096 2013-06-19 03:47 mysql

changed permissions
sudo chmod -R 755 /var/lib/mysql/
drwxr-xr-x  5 mysql   root    4096 2013-06-19 03:47 mysql

/etc/init.d/mysql restart> 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql
start: Job failed to start

I have also tried> 
sudo chown mysql:root /var/lib/mysql/ -R
sudo chmod g+rw /var/lib/mysql/ -R
sudo /usr/sbin/mysqld --skip-grant &

no success

---

### Post by sushi80 on 2013-06-19
check also the system logs

dmesg|grep myslq

my mysyql folder has this permission
drwxr-xr-x. 5 mysql   mysql   4096 Mar 15 12:26 mysql

can you try start using "mysqld" insted of "mysql"

sudo service mysqld start

I know that is not a real solution but maybe you have to consider to backup your db and remove and reinstall mysql

---

### Post by siddharth007 on 2013-06-19
```
changed mysql

cd /var/lib# ls -al
drwxrw----  5 mysql   root    4096 2013-06-19 03:47 mysql

changed permissions
sudo chmod -R 755 /var/lib/mysql/
drwxr-xr-x  5 mysql   root    4096 2013-06-19 03:47 mysql

```

From what i see in your post,the problem might be improper permissions to the mysql datadir (by default,/var/lib/mysql).It should be something like this

```

cd /var/lib# ls -al

drwx------  5 mysql **mysql** 4096 Jun 14 17:58 mysql

```

The group owner should be 'mysql' and not 'root'. So you have to do this
```

chown -R mysql:mysql /var/lib/mysql

```
 
Restart the mysql service after setting the permissions.All the best

---

### Post by monkeybrain2012 on 2013-06-19
Have you try "sudo service mysql start"?

If I use the command "sudo /etc/init.d/mysql start" It doesn't connect
```
$ sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
monkeybrain@ubu1204:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

But starting it with 
```

sudo service mysql start
```

It works just fine.

```
$ sudo service mysql start
mysql start/running, process 3263
monkeybrain@ubu1204:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 36
Server version: 5.5.31-0ubuntu0.12.04.2 (Ubuntu)

Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

---

