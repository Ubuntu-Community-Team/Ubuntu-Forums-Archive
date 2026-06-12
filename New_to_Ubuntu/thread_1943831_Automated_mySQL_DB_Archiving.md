---
title: "Automated mySQL DB Archiving"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by nogi on 2012-03-20
When I used to have a QNAP NAS running mySQL, I had a script ([http://forum.qnap.com/viewtopic.php?t=15628](http://forum.qnap.com/viewtopic.php?t=15628))   that ran nightly that made a backup of the databases (files had .sql  extension). There were 2 folders in the backup path (e.g. Current,  Archive). The sql file in Current would be zipped and moved to archive  and a new sql file was placed into Current.

I've moved MySQL onto a Ubuntu VM under esxi. How can I get something similar  working under Ubuntu?At the moment I am just taking snapshots but that's a little over the top. I've done some searches here and seen threads around mysqldump but they are a little beyond my linux knowledge. I'm just wanting an easy to configure script that can run every night.

---

### Post by TeoBigusGeekus on 2012-03-20
Just create a script with
```
mysqldump -u Yourusername -pYourpassword nameofthedbtobebackedup > /path/backupfile.sql
```
and use cron to run it whenever you want.

---

### Post by nogi on 2012-03-20
Ok, but what about the rest of the stuff that other script does like archive the previous backup? Sorry for asking the obvious but some of these server side things are fairly new to me.

---

### Post by TeoBigusGeekus on 2012-03-20
You could do something like this:
```
mv /path/backupfile.sql "/path/backupfile$(date).sql"
mysqldump -u Yourusername -pYourpassword nameofthedbtobebackedup > /path/backupfile.sql
```
Your old backup will be renamed backup12-12-12.sql (ie. its name plus the date of the backup) and a new one will be created.

---

### Post by Cheesemill on 2012-03-20
I use the AutoMySQLBackup script.

From their website:

                **Description**

                          AutoMySQLBackup  with a basic configuration will create Daily, Weekly and Monthly backups  of one or more of your MySQL databases from one or more of your MySQL  servers.

Other Features include:
- Email notification of backups
- Backup Compression and Encryption
- Configurable backup rotation
- Incremental database backups

[http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

Edit - Just had a look and it's in the repos (although I use the latest version from their site), you can use 'man automysqlbackup' after installation for instructions.

---

