---
title: "New server build using 7.10"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by wafflcommish on 2008-05-09
First post.  Just built a server using 7.10 (haven't downloaded the new version yet).  This is for the purpose of developing a database in mySQL which will eventually be used for the purpose of a website for my fantasy football league.  Here's my question: My server has 2 hard drives, an 80-GB "system" drive and a 250-GB "data" drive.  How do I configure mySQL and / or phpMyAdmin to use the second hard drive to store the data?

Thanks,

Brian

---

### Post by Monicker on 2008-05-09
The default data dir for mysql is specified in /etc/mysql/my.cnf

```
datadir         = /var/lib/mysql
```


Make a backup copy of that file, modify the line above, and then restart mysql.  Also, make sure that the mysql user has ownership of the data directory

sudo chown mysql.mysql /mysql/datadir

EDIT:  I just realized something else.  The mysql system database is created in /var/lib/mysql/mysql during the install.  You will need to move that directory if you change the default data directory.

```
sudo mv /var/lib/mysql/mysql /mysql/datadir
```

---

### Post by wafflcommish on 2008-05-13
Thank you for the tips.  I will try them and let you know what happens.  Any pointers for a new web designer?  :-)  Don't worry, I'll work my way through that one.  I was able to teach myself MS Access and VB for Apps, I'll take a crack at this too.

---

### Post by wafflcommish on 2008-05-18
Okay, so I was able to access the second drive and made the aforementioned changes.  Now, when I go to phpmyadmin and try to login, I receive "Error #2002 -- The server is not responding (or the local mySQL server's socket is not correctly configured.)"  Help!

---

### Post by wafflcommish on 2008-05-22
From another forum, I found a thread to try the 'mysqld' command.  Here's what it comes up with:

root@server1:/etc/init.d# mysqld
080522  6:58:40  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

Any ideas?

Thanks for your help.

---

### Post by wafflcommish on 2008-06-27
Thanks for your help.  With that, and some other tweaking (not exactly sure what I tweaked in general), that part is now working.  Only trick now is with phpmyadmin.  When I try to go to the site for phpmyadmin, I get the following: You have chosen to open (null), which is a PHTML file from: [http://localhost](http://localhost).  It then asks me what I want to use to open the file.

Call me Dazed and Confused on this one.

---

### Post by wafflcommish on 2008-11-20
I have upgraded to 8.04, and still am unable to redirect the datadir directory.  Every time I do, mysqld fails to start.  What could I be missing?  I'm about ready to try another flavor of Linux!

---

### Post by wafflcommish on 2008-12-09
Have solved the issue.  Here's what I did: after moving the database and setting the permissions, I had to configure AppArmor (the firewall) appropriately.  In the /etc/apparmor.d directory, look for either usr.sbin.mysql or usr.sbin.mysqld and edit this file.  You will need to add lines to the file to mark the new location of your data directory, as follows: (my data directory is /data/mysql) 
/data/mysql/ r,
/data/mysql/** rwk,
Write the changes, and restart apparmor with the /etc/init.d/apparmor start command.  Then restart mysql with /etc/init.d/mysql start.  You may need to reboot.  I did, then added some tables to my database, comparing the old directory to the new at the command line, and was up & running.

---

