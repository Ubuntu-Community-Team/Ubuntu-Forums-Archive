---
title: "How to Share MySQL data on dual boot PC?"
date: 2009-02-11
forum: Programming Talk
---

### Post by l1th1um on 2009-02-11
Hi All.

I'm using Intrepid and XP. I working as freelance programmer, so I always using PHP, MySQL, etc. I'd DocumentRoot set the htppd.conf, so it set to the data on windows partition. But I've problem when sharing MySQL data. I've edit my.cnf file

```

datadir      = /media/_home/xampp/mysql/data

```

But when i restart MySQL it get failed. 

Anybody have solution for this?

---

### Post by patryk77 on 2009-02-11
I really wouldn't recommend it, but you can always install windows EXT2/3 drivers and point mysql to wherever you mount the Linux drive.

Another option you could envisage is running Windows as a Guest OS in Virtualbox, depending on your usage. Then you could access the MySQL server running under Ubuntu.

It's what I do on my laptop.

---

### Post by unutbu on 2009-02-12
As of Intrepid (or maybe Hardy), mysql uses apparmor to restrict the files that mysql can read and write to. If you want mysql to be able to access /media/_home/xampp/mysql/data, then you'll need to edit /etc/apparmor.d/usr.sbin.mysqld by adding these two lines:

```
/usr/sbin/mysqld {
  ...
[COLOR="Red"]  /media/_home/xampp/mysql/data/ r,
  /media/_home/xampp/mysql/data/** rwk,[/COLOR]
}


```


For more info on apparmor see [http://ubuntuforums.org/showthread.php?p=6353882#post6353882](http://ubuntuforums.org/showthread.php?p=6353882#post6353882)

---

### Post by agsel on 2010-07-04
I have used mysql in windows. Now I want to access the same data within Ubuntu 10.04. I have installed mysql-server-5.1.41 and client. I have copied data from windows to a separate NTFS partition. If I change /etc/mysql/my.cfg and set datadir to my NTFS partition, I get permission denied error (in mysql error log). I have updated apparmor configuration for mysqld. Has anyone got it working?

I haven't modified anything except for datadir in /etc/mysql/my.cfg

datadir = /media/Storage/Data/MySQL

In /var/log/mysql/error.log I get:

/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
100704 17:49:13 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
100704 17:49:13  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

in /etc/apparmor.d/usr.sbin.mysqld added rows:

  /media/Storage/Data/MySQL/ r,
  /media/Storage/Data/MySQL/** rwk,

Any ideas?

---

### Post by agsel on 2010-07-05
I now noticed the forum where I posted my problem (I searched for the topic and replied instead of creating a new topic). Is it a correct place for the question?

---

