---
title: "mysql has turned into myheadache"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by infosys on 2008-05-20
During boot-up MySQL fails to start. It used to work just fine though, don't know what changed.

 I’ve gone through several different forums, and the two main problems I’ve seen posted were: 1. mysql-server was not installed, and I’ve verified mine is. 2. In the /etc/mysql/my.cnf file the bind-address was incorrect, normally due to the IP address of the server changing. I’ve verified mine is set to the loop-back, 127.0.0.1.

When I try to start MySQL manually, by using the command “sudo /etc/init.d/mysql start”, it fails. When I try to start MySQL manually, by using the command “sudo mysql start”, it fails giving “ERROR 2002 (HY000): Can’t connect to local MySQL server through socket ‘/var/run/mysqld/mysqld.sock’ (2)”.

I've also checked the /var/log/mysql.err and mysql.log files, but they are both empty.

Anybody know what I can do or where I should look?

I’ve had some permissions problems in the past, and my guess is this is somehow related to permissions even though I have no reason to belive so.

---

### Post by Monicker on 2008-05-20
Umm.  Why are you opening another thread about this?  I responded to your earlier post.

[http://ubuntuforums.org/showthread.php?t=801674]("http://ubuntuforums.org/showthread.php?t=801674")

---

### Post by infosys on 2008-05-21
Hummm, sorry about the double-post, not exactly sure what happend there. I can't find any way to remove this one eaither, is there a way?

---

### Post by nicedude on 2008-05-21
Not sure about how to delete it but you can edit it and change title to "oops sorry for doublepost" or something like that.

---

### Post by infosys on 2008-05-21
Maybe I'm just being dense, but for the life of me I can't seem to find anywhere to change the title of the thread. I can change the titles to my posts, but not the whole thread.:confused:

---

