---
title: "Can't connect to local MySQL server through socket ..."
date: 2012-04-12
forum: New to Ubuntu
---

### Post by jimeast on 2012-04-12
[SIZE=2]I installed Ubuntu about a week ago after a couple of days I installed Xampp/lampp using the terminal window I can start and stop mysql and apache.  I can use command and connection parameter options like mysql --version , mysql --protocol and mysql -u username -p but when I try to log in I get [/SIZE]


[SIZE=2]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[/SIZE]
[SIZE=2]I looked in a folder var/run and found a mysql there I'm wondering does Ubuntu come with mysql already installed?  Did I screw something up by installing lampp?[/SIZE]

---

### Post by greenpeace on 2012-04-12
Hi, what exactly do you mean by "log in"?

To access the mysql db on the command line, you just run the mysql command with username and password arguments:

```
greenpeace@gppg:~$ mysql -u username -p
```

you will be prompted for your password:

```
Enter password: 
```

and you should then see the welcome message:

```

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 44291
Server version: 5.0.95-0ubuntu1-log (Ubuntu)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

```
and then the mysql prompt (where you enter your commands):

```

mysql> 

```

What do you see on your system?  It is very unlikely that you have caused any problems by installing the lampp packages.

---

### Post by jimeast on 2012-04-13
[SIZE=2]I don't get the welcome message or the prompt I get this:[/SIZE]

[SIZE=2]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/SIZE]

---

### Post by greenpeace on 2012-04-13
> **jimeast said:**
> [SIZE=2]...I get this:[/SIZE]

[SIZE=2]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/SIZE]

according to the MySQL docs[0]:

[INDENT]*The error (2002) Can't connect to ... normally means that there is no MySQL server running on the system or that you are using an incorrect Unix socket file name or TCP/IP port number when trying to connect to the server. You should also check that the TCP/IP port you are using has not been blocked by a firewall or port blocking service.*[/INDENT]

What do you get if you see in the terminal if you run the following command?

```
sudo service mysql status
```

[0] [http://dev.mysql.com/doc/refman/5.5/en/can-not-connect-to-server.html]("http://dev.mysql.com/doc/refman/5.5/en/can-not-connect-to-server.html")

---

### Post by enkay009 on 2012-04-13
First check which mysql client you're using.

```
which mysql
```

If this is not the one that came with LAMPP, then use the one that came with LAMPP by specifying it's absolute path.

mysql clients look for their configuration file (my.cnf) in hardcoded places. The configuration file (among other things) defined where the server will put the socket file and where the client will look for it.

What I think is happening is that you have two mysql clients installed: one from the repo and one from LAMPP. And you're using the one from the repo so by default it is expecting the socket in a certain location but it doesn't exist.

If that's not the problem, then check if the socket exists (the path mysql complained about) and whether your user has access to it.

And another problem could be that you have another mysql server running on the same machine. It's not a huge problem, you can simply change the PORT one them run on.

---

### Post by pradeepsixer on 2012-04-17
You did not start up the mysql server i guess.

1. All you need to do is go to /opt/lampp/sbin and execute 
./mysqld -u root

Or else, you can also start lampp by ./lampp start

2. After that,go to /opt/lampp/bin and execute ./mysql -u root

---

