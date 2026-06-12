---
title: "[SOLVED] C#/MySQL/Mono remote connection??"
date: 2008-09-05
forum: Programming Talk
---

### Post by LRT on 2008-09-05
i am developing a c# winform application on windows xp (using visual studio 2008) that will read/write from/to a MySQL database sitting on an ubuntu server. i'm running Mysql 5.0.51a and Mono 1.9.1 both on Ubuntu 8.04 server. i am very new to Mono so i'm not sure how this is all suppose to work. 

i can already succesfully compile/build and execute the c# code FROM the ubuntu server. this code can read/write to the MySQL database sitting on the same server.

**my question is**: can i compile/build and execute the c# code from my windows xp machine (using visual studio 2008)?? should this code be able to connect to the mysql database on the ubuntu server???... because right now i can't get it to do that.

---

### Post by Zugzwang on 2008-09-05
> **LRT said:**
> **my question is**: can i compile/build and execute the c# code from my windows xp machine (using visual studio 2008****)?? should this code be able to connect to the mysql database on the ubuntu server???... because right now i can't get it to do that.

Sure. You will need to change your program to connect to the server (so not using "localhost" as address doesn't work anymore) and you will need to set the user rights in MySQL accordingly to allow connections from other computers.

---

### Post by LRT on 2008-09-05
ok. i already changed 'localhost' to the name of my server. i'm looking at user rights and privileges right now. thanks!

---

### Post by LRT on 2008-09-05
ok, got it working!!... these docs helped..

[http://dev.mysql.com/doc/refman/5.0/en/grant.html](http://dev.mysql.com/doc/refman/5.0/en/grant.html)
[http://dev.mysql.com/doc/refman/5.0/en/privileges.html](http://dev.mysql.com/doc/refman/5.0/en/privileges.html)
[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

(MySQL has amazingly clear and easy to understand documentation!)

---

