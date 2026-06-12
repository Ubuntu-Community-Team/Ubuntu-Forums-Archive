---
title: "[SOLVED] Reset MySQL Password"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by bprof on 2008-07-20
Hello,

My mysql (5.0.45) has a password I know the password but when I tried to used it to login to phpmyadmin I got the folllowing:

```
#1045 - Access denied for user 'root'@'localhost' (using password: NO)
```

I have tried the solution described [here]("https://help.ubuntu.com/community/MysqlPasswordReset") to reset the password, but when I ran this command:

```
sudo mysqld --skip-grant-tables &
```

I got this and I wasn't able to run any further command 

```
080720 16:29:40  InnoDB: Started; log sequence number 0 156301
080720 16:29:40 [Note] mysqld: ready for connections.
Version: '5.0.45-Debian_1ubuntu3.3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution

```

So I opened a new terminal and ran all the other commands successfully.

```
Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE user SET Password=PASSWORD('NEWPASSWORD') WHERE User='root';
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> FLUSH PRIVILEGES; exit;
Query OK, 0 rows affected (0.00 sec)

Bye
```

Tried to login from the command prompt and from phpmyadmin and I'm still getting the same message:

```
#1045 - Access denied for user 'root'@'localhost' (using password: NO)
```

I tried with the new password, and without password and same thing.

Any ideas?

Thank you,

---

### Post by pavel989 on 2008-07-20
did u set up a root account?

---

### Post by bprof on 2008-07-20
Yes I have a root account. And I was able to access mysql yesterday, but not today. All the steps I described were done after I failed to login.

---

### Post by pavel989 on 2008-07-20
any chance u have 2 installs?

---

### Post by bprof on 2008-07-20
No, I have only one install!

---

### Post by cariboo on 2008-07-20
There is another way to set a new root password for mysql. In a terminal type:

```
sudo dpkg-reconfigure mysql-server-5.0
```

This will bring up the screen that asks you to enter a root password.

Jim

---

### Post by bprof on 2008-07-21
The easiest by far. Thank you so much!

---

