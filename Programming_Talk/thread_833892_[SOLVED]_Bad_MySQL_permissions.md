---
title: "[SOLVED] Bad MySQL permissions"
date: 2008-06-19
forum: Programming Talk
---

### Post by Bionic Apple on 2008-06-19
During the last few days, I have been learning PHP.  It has been great, until I started MySQL.  I downloaded all the packages needed from the repositories.  However, this error always comes up when I try to do the first step in a tutorial:

```
mysql> CREATE DATABASE testdb;

ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'testdb'

```

If I should know the reason for this (beginner or not), then the MySQL tutorials that I have followed obviously aren't that great...

---

### Post by ad_267 on 2008-06-19
Are you logged in to mysql as the root user? (Not as in using sudo but your mysql root user). You need to be root to create a database usually.

Start mysql like this:
```
mysql -u root -p
```
and enter the root password

---

### Post by Bionic Apple on 2008-06-19
I put it in and got this:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```
[B]
UPDATE:[/B] Nevermind, it was the wrong password.  Thanks, I did not know that I have to enter in those extensions.

---

