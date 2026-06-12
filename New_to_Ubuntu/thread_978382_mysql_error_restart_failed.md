---
title: "mysql error restart failed"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-11
I loaded up lamp. I ran some updates. Now when i try to access mysql it says cannot connect too mysql. I went to the command prompt and typed in 

/etc/init.d/mysql start and recieve [failed]

I see other people are having this problem but don't know how to fix it.

I saw in some file while i was looking around I believe i say it in syslog something about mysql needing port 33xx something needing to be open. Somewhere i saw something about a  way too fix this. I don't know what files I am looking for. Something about a system file that acts like a port forwarding. I need some help. I am new too linux and i'm trying to get my ubuntu desktop 8.10 running a web server so I can practice. I believe this is beyond my knowledge at the moment for linux. If anyone can help me it would be greatly appreciated. I will need file name directories and way to access them ( possibly command line ) I am still learning how to navigate linux so i must stress lamens terms. 

I believe the other programs in lamp are working fine. I can view var/www from dynamicdns i have setup. Only thing not working is MySQL. If you need additional information from me too help. Please let me know what file and where its located so I can get back too you for further diagnosis. Thank you for any help you can give me.

---

### Post by shanep-server on 2008-11-11
mysqld[6670]: 081111  2:53:15 [Warning] Can't create test file /var/lib/mysql/shanep-desktop.lower-test

 mysqld[6670]: 081111  2:53:15 [Warning] Can't create test file /var/lib/mysql/shanep-desktop.lower-test

 mysqld[6670]: 081111  2:53:15 [Warning] One can only use the --user switch if running as root

 mysqld[6670]: 081111  2:53:17  InnoDB: Operating system error number 13 in a file operation.

 mysqld[6670]: InnoDB: The error means mysqld does not have the access rights to

 mysqld[6670]: InnoDB: the directory.

 mysqld[6670]: InnoDB: File name ./ibdata1

 mysqld[6670]: InnoDB: File operation call: 'open'.

 mysqld[6670]: InnoDB: Cannot continue operation.

 mysqld_safe[6687]: ended

 /etc/init.d/mysql[6830]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in

 /etc/init.d/mysql[6830]: Could not open required defaults file: /etc/mysql/debian.cnf

 /etc/init.d/mysql[6830]: Fatal error in defaults handling. Program aborted

 /etc/init.d/mysql[6830]: 

This is some of what my syslog shows. If that helps at all.

---

### Post by cariboo on 2008-11-11
What are you trying to do when you get this error:

> mysqld[6670]: 081111 2:53:15 [Warning] Can't create test file /var/lib/mysql/shanep-desktop.lower-test

Jim

---

### Post by shanep-server on 2008-11-11
honestly I was trying to accomplish was restart or trying to start my mysql server so I could get an error to type out here an try to get some help. I didn't know my mysql server was down until i installed webmin. Then when i went to the mysql part it said it couldn't start mysql. So i tried to restart mysql and it failed. I was just trying to recreate what happened to give people an idea of whats going on in my system. I'm still new too lookin around ubuntu or linux in general so i'm kind of stumbling my way about at the moment. Not all of my logs will make sense. Thats what i got you great people for. I wasn't sure if I should be looking for errors in my syslog or my daemon.log

---

