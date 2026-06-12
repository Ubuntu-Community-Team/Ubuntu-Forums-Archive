---
title: "MySQL Drag &amp; Drop of Database possible?"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by deidara2 on 2014-04-10
Hello Community,

I have several problems with MySQL and phpmyadmin, so I decided to reinstall them. However the databases, who are already in use in mysql need to be saved.
I am a windows user, so can I just drag and drop the whole database in "/var/lib/mysql/DATABASE" on my Desktop (with Filezilla), then reinstall mysql and drag it in again? Or is this not possible?

Greetings
Deidara

---

### Post by cariboo on 2014-04-10
Using mysqldump is the preferred way to backup and restore mysql databases. There is a howto [here]("http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/").

You can also use phpmyadmin to backup your databases, have a look at this [howto]("http://www.rackspace.com/knowledge_center/article/how-to-backup-your-mysql-database-with-phpmyadmin").

---

### Post by deidara2 on 2014-04-11
> **cariboo907 said:**
> Using mysqldump is the preferred way to backup and restore mysql databases. There is a howto [here]("http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/").

You can also use phpmyadmin to backup your databases, have a look at this [howto]("http://www.rackspace.com/knowledge_center/article/how-to-backup-your-mysql-database-with-phpmyadmin").

The problem with mysqldump is, that I need to login to make a backup. But I need to reinstall mysql because, when I installed it, there came up a error, and no matter what password I try, it don't have the permissions for anything in mysql, even as root. So I have to backup it with a way, where I don't need to enter a password. Is there such a possibility?

---

### Post by steeldriver on 2014-04-11
Have you tried reconfiguring the mysql-server package? it should prompt you to set a new mysql root password

```
sudo dpkg-reconfigure mysql-server-5.5
```

(the number on the end may differ depending what version of Ubuntu you are running). That's certainly the first thing you should try if you are having mysql password problems.

You *can* drag and drop the /var/lib/mysql directory - but you'd need root privileges i.e. run the nautilus file manager from a terminal using

```
gksudo nautilus
```

Be aware that if you do that, the 'Home' that you see will be root's Home (/root) not your own Home (/home/username).

FWIW reinstalling the mysql server package shouldn't affect any of your  actual data - although you are absolutely right to back it up anyway,  just in case. If I really couldn't use mysqldump, I think I would rename the directory from the command line e.g.

```

sudo service mysql stop

sudo mv /var/lib/mysql /var/lib/mysql_old

sudo apt-get install --reinstall mysql-server

```

Reinstallation will create a new /var/lib/mysql directory AND start the service, so before moving your data back you'd want to stop it again

```

sudo service mysql stop

sudo mv /var/lib/mysql_old /var/lib/mysql

```

This will overwrite the newly installed directory with your old directory. After that you should be able to restart the service

```

sudo service mysql start

```

---

### Post by deidara2 on 2014-04-11
> **steeldriver said:**
> Have you tried reconfiguring the mysql-server package? it should prompt you to set a new mysql root password

```
sudo dpkg-reconfigure mysql-server-5.5
```

(the number on the end may differ depending what version of Ubuntu you are running). That's certainly the first thing you should try if you are having mysql password problems.

You *can* drag and drop the /var/lib/mysql directory - but you'd need root privileges i.e. run the nautilus file manager from a terminal using

```
gksudo nautilus
```

Be aware that if you do that, the 'Home' that you see will be root's Home (/root) not your own Home (/home/username).

FWIW reinstalling the mysql server package shouldn't affect any of your  actual data - although you are absolutely right to back it up anyway,  just in case. If I really couldn't use mysqldump, I think I would rename the directory from the command line e.g.

```

sudo service mysql stop

sudo mv /var/lib/mysql /var/lib/mysql_old

sudo apt-get install --reinstall mysql-server

```

Reinstallation will create a new /var/lib/mysql directory AND start the service, so before moving your data back you'd want to stop it again

```

sudo service mysql stop

sudo mv /var/lib/mysql_old /var/lib/mysql

```

This will overwrite the newly installed directory with your old directory. After that you should be able to restart the service

```

sudo service mysql start

```

Okay I reconfigured the password and logged into mysql with ```
mysql -u root -p
``` Then I entered the password, I just set up. Terminal says "Access denied." 
I tried to log in again, but now just clicked ENTER when it asked for the pw and then it accepted that. Now I tried to create a new database. the terminal answered this 
```

mysql> create database gamepanel;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'gamepanel'

```
After that I tried your second command. The terminal told me that "gksudo" isn't installed, so I installed it and run the command again. The termnial outputs this ```

root@Ubuntu-1204-precise-64-minimal ~ # gksudo nautilus
connect /tmp/.X11-unix/X0: No such file or directory
connect /tmp/.X11-unix/X0: No such file or directory
connect /tmp/.X11-unix/X0: No such file or directory
connect /tmp/.X11-unix/X0: No such file or directory

(gksudo:25178): Gtk-WARNING **: cannot open display: localhost:10.0

```

Now I don't now what to do. I tried to reinstall mysql, but I always get the error. Maybe it's because I have some servers currently running, which are connected to a mysql database? I think I need to remove all traces of mysql from my rootserver and reinstall it completely.

I tried to remove and reinstall mysql. However...it seems that I can't install it again.
```
root@Ubuntu-1204-precise-64-minimal ~ # apt-get remove --purge mysql-server mysql-client mysql-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mysql-client is not installed, so not removed
Package mysql-common is not installed, so not removed
Package mysql-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
root@Ubuntu-1204-precise-64-minimal ~ # apt-get install mysql mysql-server      Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package mysql


```

EDIT:
I just did ```
apt-get install mysql-server
```
That worked. My problem is solved. Thanks for your help!

---

