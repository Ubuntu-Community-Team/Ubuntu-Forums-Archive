---
title: "MySQL Import"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by swanside on 2012-12-16
Hello.
Can anybody tell me where MySQL Import file would be please?
I did apt-get install MYSQL and its all running, but I have a script to import files into mysql and I need to find the path to the MySQL Import file?
 
Cheers
Swanny

---

### Post by squakie on 2012-12-16
You're saying you have MySQL installed, and you have a separate file (the data, schema, etc.) to import, correct?  Then that file should be where ever you put it when you (a) created it (b) downloaded it (c) placed when you copied from another media.

---

### Post by swanside on 2012-12-17
I have MySQL installed on my Ubuntu server.

I have a script on another server that when a certain file is received, it runs a vbs file which has the IP address to my Ubuntu server.

This then needs to run the MySQL import bat file, it will then import the cvs file that I get over to my server using the IP address and import it into the correct table in MySQL.

The only problem is, I can not find the mysql_import bat file on my Ubuntu server

Swanny

---

### Post by squakie on 2012-12-17
A .bat file is a Windows thing - no such animal in Linux.  There may be some sort of shell script that does something similar, but you'd have to do some looking.  I'm not so sure vbs runs on Ubuntu (isn't that visual basic script?).  You probably need to look for ubuntu alternatives to your script file or convert it yourself.

How many lines does the vbs bat file contain?  Could you attach it here in a reply?

---

### Post by swanside on 2012-12-17
Hiya,
The vbs file is on a. Windows server where the cvs file lands.
The windows computer will run the vbs file. The vbs file has the IP address and location of the MySQL import file, sorry, I thought it was a bat file,I think that is what it is on the windows machine, so I was assuming there was also one on the Ubuntu.
All I need to find out then, in my Ubuntu file structure, if there is a mysql_import, similar to is there a mysql_dump?

Cheers
Swanny

---

### Post by squakie on 2012-12-17
I think I would look in the MySQL documentation for Linux - perhaps even doing a net search with:

linux MySql import script

If you already have such a bat file in existence in Windows, attach a copy of it in a reply back here (you can either use the paper clip to attach it, or you can copy it's contents and paste in back here in code tabs (see the pound sign).

If you have that, we could take a look at it and see if we can work something out.

Perhaps this is something that may help?  [http://www.cyberciti.biz/faq/import-mysql-dumpfile-sql-datafile-into-my-database/](http://www.cyberciti.biz/faq/import-mysql-dumpfile-sql-datafile-into-my-database/)

---

### Post by Wim Sturkenboom on 2012-12-17
> **swanside said:**
> 
All I need to find out then, in my Ubuntu file structure, if there is a mysql_import, similar to is there a mysql_dump?
The reverse of mysql-dump is the mysql command with some arguments and a redirect as described in squakie's link (specifically step # 3). You need to tailor it to your needs.

---

### Post by SeijiSensei on 2012-12-17
Isn't there a way to have the VBS script talk directly to MySQL, presumably using the [MySQL ODBC connector for Windows]("http://dev.mysql.com/downloads/connector/odbc/")?  The method you've described has way too many unnecessary intermediate steps.  Just have the VB script open a connection to MySQL and post the data directly.

---

### Post by drdos2006 on 2012-12-17
This is the command from a terminal on the server to import the 'dumped' SQL file. I use Webmin to set up the server database as a "clean" file, because the name of the database being restored has to exist before the database can be restored.

From the server CLI ype : mysql -u root -p (without password) cms < /media/sdb2/sql-backup/cms.sql
Enter password.

Do not type in the password until you are asked.
The name of the "clean" database on the server is "cms".


There is a Linux script available if you need it.

regards

---

