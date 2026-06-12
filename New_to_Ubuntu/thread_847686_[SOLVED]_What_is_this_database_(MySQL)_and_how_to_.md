---
title: "[SOLVED] What is this database (MySQL) and how to configure it?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-02
What is this database in amarok ? During the first run wizard I chooose MySQL as the database . And now whenever I start amarok this error message shows up:

> MySQL reported the following error:
Can,t connect to local MySQL server through
socket '/var/run/mysqld.sock'(2)Can someone please tell me what this is and how to solve it?
Many thanks.

---

### Post by Darkade on 2008-07-02
I don't use amarok but i've used MySQL. First of all. do you have MySQL installed? and if you do, is your user setup in MySQL by default just root has a MySQL Account

---

### Post by bhadotia on 2008-07-02
Yes, MySQL client is installes - I checked it in synaptic?
I cannot understand what you are talking about this user and root issue . Please be a little more detailed.

---

### Post by Darkade on 2008-07-02
Ok, MySQL is a database administrator. It has users leves and each user has his own databases. By default only root has a MySQL enabled account. So since you are using Amarok with your user you may not have access to MySQL, and thus you can't make a database for whatever Amarok is trying to use it

---

### Post by LowSky on 2008-07-02
here you go

[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

---

### Post by bhadotia on 2008-07-02
So how what should I do to be able to access the database?

---

### Post by bab1 on 2008-07-02
I think mySQL is a little heavy duty for this app.  The client (app) is trying to connect locally and there is no socket setup.  Wasn't mySQL originally selected in error?  If so I would remove the package and reinstall using the default database.

---

### Post by Darkade on 2008-07-02
> **bab1 said:**
> I think mySQL is a little heavy duty for this app.  The client (app) is trying to connect locally and there is no socket setup.  Wasn't mySQL originally selected in error?  If so I would remove the package and reinstall using the default database.

I would say that's what you should do. because you can add your user to MySQL but I think it's kindda point less. if anyway you want to add your user to MySQL check [this]("http://dev.mysql.com/doc/refman/5.1/en/create-user.html") howto

---

### Post by bab1 on 2008-07-02
I thinks we are getting a bit off track. Bhadotia is the user and he appears to be the only user.  I'm saying the application (amarok) is trying to connect to mySQL and cant.  Bottom line:  I think Bhadotia is better off with SQLite in the beginning.  I looked aat the site  LowSky reccomended and it is a good one.

---

### Post by bhadotia on 2008-07-02
I had a look at the link lowsky gave . Whenever I do this a error comes:
```
abhishek@ubuntu:~$ mysqladmin -u root password PASSWORD
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
I type the password I set when I was installing mysql server. What am I doing wrong?

---

### Post by Darkade on 2008-07-02
> **bab1 said:**
> I thinks we are getting a bit off track. Bhadotia is the user and he appears to be the only user.  I'm saying the application (amarok) is trying to connect to mySQL and cant.  Bottom line:  I think Bhadotia is better off with SQLite in the beginning.  I looked aat the site  LowSky reccomended and it is a good one.
yes that's right. my point is that he can't access if his account ain't set up

---

### Post by bab1 on 2008-07-02
Did you literally use the password called PASSWORD?  Try
```
abhishek@ubuntu:~$ mysqladmin -u root -p "yourpassordthatyoucreated"
```

Send us the results/

---

### Post by bab1 on 2008-07-02
There should be a root account if he installed correctly

---

### Post by bhadotia on 2008-07-02
Alright after searching the net a bit I have got through the passwrd problem but now another problem has popped up . Look here:
```
abhishek@ubuntu:~$ mysqladmin -u root -p hara
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
abhishek@ubuntu:~$ sudo pkill -9 mysql
abhishek@ubuntu:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
abhishek@ubuntu:~$ mysqladmin -u root -p hara
Enter password: 
mysqladmin: Unknown command: 'hara'
abhishek@ubuntu:~$ mysqladmin -u root -p hara
Enter password: 
mysqladmin: Unknown command: 'hara'
```
Where hara is my current password.

---

### Post by bhadotia on 2008-07-02
I think I did something wrong over there I used the option '-p' in front of my password. So the first problem still remains. 
Any suggestions?

---

### Post by bab1 on 2008-07-02
Oops,  Use the same command except the actual password -- wait until you have the prompt.  ie; abhishek@ubuntu:~$mysqladmin -u root

---

### Post by bhadotia on 2008-07-02
But that also did not work :
```
mysqladmin  Ver 8.41 Distrib 5.0.51a, for debian-linux-gnu on i486
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Administration program for the mysqld daemon.
Usage: mysqladmin [OPTIONS] command command....
  -c, --count=#       Number of iterations to make. This works with -i
                      (--sleep) only.
  -#, --debug[=name]  Output debug log. Often this is 'd:t:o,filename'.
  -f, --force         Don't ask for confirmation on drop database; with
                      multiple commands, continue even if an error occurs.
..................................
..................................
```
Above is the output of that command- there was a long list so I did not post the whole output.

---

### Post by bab1 on 2008-07-02
I'm not sure what your problem is.  I have never had any problems.  MySQL usually installs with the root account having NO password.  You get to give it the password once you connect.  I have done this many times.  Try reading this:  [http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

---

### Post by bhadotia on 2008-07-02
I think we've got it .Look here :
```
 mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 13
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 
```Atleast now I have the prompt.
I'll see what I can do .
And thanks for that last  link.

---

### Post by bab1 on 2008-07-02
yes!

---

### Post by bhadotia on 2008-07-02
Thank You very much , I've successfully configured amarok for use with MySQL.

---

