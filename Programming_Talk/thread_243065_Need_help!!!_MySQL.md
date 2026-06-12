---
title: "Need help!!! MySQL"
date: 2006-08-24
forum: Programming Talk
---

### Post by Blacktalon on 2006-08-24
Hello,
I am needing help with MySQL, I have installed it from synaptics and whenever I try to run a tutorial on Ruby on Rails I get this error:
'/var/run/mysqld/mysqld.sock' (2)

Please can anyone help me.


~BT

---

### Post by Woei on 2006-08-25
> **Blacktalon said:**
> Hello,
I am needing help with MySQL, I have installed it from synaptics and whenever I try to run a tutorial on Ruby on Rails I get this error:
'/var/run/mysqld/mysqld.sock' (2)


You'll have to give us more relevant output than that, otherwise we're as much in the dark as you are. Are you sure MySQL is running (sudo /etc/init.d/mysql restart). Have you [configured some users](http://dev.mysql.com/doc/refman/5.0/en/post-installation.html) for your MySQL server ? As the error above indicates, the Rails framework is trying to connect to MySQL locally over a socket. Is the MySQL server process listening on localhost (display the listing of netstat --tcp --listen -p) ? Did you configure Rails correctly ?

---

