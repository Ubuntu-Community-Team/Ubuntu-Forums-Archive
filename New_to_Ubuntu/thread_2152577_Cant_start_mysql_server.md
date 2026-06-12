---
title: "Cant start mysql server"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by AvengerX9 on 2013-06-08
Im trying to start or restart the mysql server from webmin but fails. I also tried from the command line 

```
sudo: /etc/init.d/mysqld start
```

Does not work either, all my sites are down and before i stopped it I noticed my databases were all gone. Even the ones that comes with phpmyadmin.

The night before I was adding a third domain to my server in the httpd.conf file and I made a folder to store the new website/domain files, but had some permission problems when I tried uploading files using ftp.

I tried this command to change the ownership of the created folder

```
sudo chown -R username:group directory
```

When I did that I noticed i start getting this kind of error before I had to enter my password

```
sudo: /var/lib/sudo owned by uid 1000, should be uid 0
```


Can anyone help me fix this, is my database lost ?

---

### Post by AvengerX9 on 2013-06-08
I also get this when I try start mysql from the command line

> roger@latonia:~$ /etc/init.d/mysqld start
-bash: /etc/init.d/mysqld: No such file or directory


> roger@latonia:~$ /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.14" (uid=1000 pid=6938 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")



> roger@latonia:~$ service mysql start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.15" (uid=1000 pid=6941 comm="start mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")


---

### Post by prodigy_ on 2013-06-08
> **AvengerX9 said:**
> ```
roger@latonia:~$ service mysql start
```
There's nothing wrong with the output. Regular accounts don't have rights to start/stop services. Try ```
sudo service mysql start
```

However, you also mentioned that your sudo executable is owned by uid 1000. Unless you made it so yourself (with **chown -R** perhaps?) your system may be broken or compromised.

As for getting things back to normal, that depends on how many changes you made trying to make your server work and how well you documented them. If you track all your changes, you can revert them one by one. If not, you probably should restore the system from a backup copy. Ideally you should never experiment on a live, production server at all. There are virtual machines that can be easily reverted back to a previous state using snapshots. 

Also you should never use chown or chmod on any system files or folders (especially with -R option) unless you're sure that you clearly understand the consequences and that there's no better way.

---

### Post by localhost8080 on 2013-06-08
first, check the /var/lib/mysql folder

if you 

ls /var/lib/mysql
then you should have a lot of folders in there - each corresponds to your database tables.
if they arent there, then you will have to restore form a backup.

assuming that those files exist, then you need to check a couple of things:

check that the mysql user has access to the folders:

ls -l /var/lib/mysql

hopefully this tells you that all the folders are owned by mysql user and mysql group.

if they arent, then you should:

sudo chown -R mysql:mysql /var/lib/mysql

try to restart mysql at this point:

sudo service mysql start

hopefully mysql starts at this point.

---

### Post by AvengerX9 on 2013-06-08
I used to be able to start and stop everything with this account before

---

### Post by AvengerX9 on 2013-06-08
> **localhost8080 said:**
> first, check the /var/lib/mysql folder
if you 

ls /var/lib/mysql
then you should have a lot of folders in there - each corresponds to your database tables.


```
roger@latonia:~$ ls -l /var/lib/mysql
total 94276
drwx------ 2 roger root     4096 Apr 15 10:57 chat
drwx------ 2 roger root     4096 Apr 15 10:45 chat2
-rw-r--r-- 1 roger root        0 Apr 12 00:19 debian-5.5.flag
-rw-rw---- 1 roger root 85983232 Jun  8 13:19 ibdata1
-rw-rw---- 1 roger root  5242880 Jun  8 13:19 ib_logfile0
-rw-rw---- 1 roger root  5242880 Jun  7 20:46 ib_logfile1
drwx------ 2 roger root     4096 Apr 12 00:20 mysql
-rw-rw---- 1 roger root        6 Apr 12 00:20 mysql_upgrade_info
drwx------ 2 roger root     4096 Apr 12 00:20 performance_schema
drwx------ 2 roger root     4096 Apr 12 00:21 phpmyadmin
drwx------ 2 roger root     4096 Apr 12 00:19 test
drwx------ 2 roger root    20480 May  4 22:30 truckstop24
drwx------ 2 roger root     4096 May 13 14:38 truckstop247
drwx------ 2 roger root     4096 May  4 15:45 truckstopguiden
drwx------ 2 roger root     4096 Apr 20 21:59 vanilla
drwx------ 2 roger root     4096 Apr 15 18:48 yourls
```


Thanks, I did what you said and it works :D

---

