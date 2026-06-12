---
title: "installing mysql with phpmyadmin"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by franco81 on 2008-06-05
Installing the LAMP stack, I'm having a few difficulties installing MySQL and phpmyadmin, perhaps someone could answer a couple of my questions as there seem to be a few different answers on google search results.

Already installed are apache2 and php5.

I install mysql using something like:
```
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```

I install phpmysadmin with:
```
sudo apt-get install phpmyadmin
```

I want to log in to phpmyadmin and start creating databases and users etc. but this is where it goes horribly wrong. Is the login for phpmyadmin:
a) the root user for mysql
b) a user in .htaccess .htpasswd

I can log in to phpmyadmin with my root user for linux, but then, that user has no permissions to add or change anything.

How do I add a root user to mysql, I've tried doing this using a few different methods but I cannot even log in to mysql as root to edit the users table, and now I cannot log in because of a mysql.sock error.

Many thanks.

---

### Post by Cypher on 2008-06-05
Try the following, login to mysql as root
```

mysql -u root

```
You should be at the mysql> prompt without any problems.
Then add a new super user that will have the authority to create database and subsequent users
```

GRANT ALL PRIVILEGES ON *.* TO 'superuser' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;

```
You can change the 'superuser' and 'password' to be anything you want, be sure to put it in single quotes.

Modify the Phpmyadmin configuration file and put this new user information in there and you should now have full reign over MySQL..

---

### Post by franco81 on 2008-06-05
Unfortunately that does not work for me, trying:
```
mysql -u root
```

results in:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```

Update:
I removed this error by changing the bind-address back to 127.0.0.1. But I am still getting an error when attempting to log in to mysql with:
```
mysql -u root
```

that is:
```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

This has persisted after removing and re installing mysql-server etc.

Thanks

---

### Post by Nepherte on 2008-06-05
Try
```
mysql -u root -p yourpassword
```

---

### Post by franco81 on 2008-06-05
Sorry, but I still get the same error (Acess denied in above post).

---

