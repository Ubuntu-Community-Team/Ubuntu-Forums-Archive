---
title: "MySQL Access Denied Issue"
date: 2010-09-25
forum: Programming Talk
---

### Post by dwhitney67 on 2010-09-25
It's been a few years since I dabbled with MySQL, and even then I interfaced to the Database using MySQL++ in a C++ application.

Anyhow, I am having trouble setting up a *regular* user to have permissions to create databases and tables.

As the MySQL root, I created a database, then a user account, and then I granted this user all privileges for this database.
```

# mysql -p
...
mysql> CREATE DATABASE dbname;
...
mysql> CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
...
mysql> USE dbname;
...
mysql> GRANT ALL PRIVILEGES ON dbname TO 'user'@'localhost' identified BY 'password';
...
mysql> FLUSH PRIVILEGES;
...

```
All of the commands above succeeded without error.

Now, when I log into MySQL as the regular user, I am unable to create a table within a database:
```

$ mysql -p
...
mysql> USE dbname;
...
mysql> CREATE TABLE test (
    -> columnOne int(11) NOT NULL,
    -> columnTwo varchar(50) NOT NULL,
    -> PRIMARY KEY (columnOne)
    -> );
ERROR 1142 (42000): CREATE command denied to user 'user'@'localhost' for table 'test'

```
What am I missing?  Is this a permissions issue with the actual database file in */var/lib/mysql*?  Does my regular user need to be made part of the *mysql* group?


P.S.  All references above to "user" and "password" are not the actual values used.

---

### Post by mrhhug on 2010-09-25
phpmyadmin makes mysql admin a breeze 

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

you will need other services installed , but usually if your installing mysql your installing the entire LAMP stack.


i added databases with authenticated users to this thing literally in less than 5 mins. its the only way to go

---

### Post by dwhitney67 on 2010-09-25
> **mrhhug said:**
> phpmyadmin makes mysql admin a breeze 

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

you will need other services installed , but usually if your installing mysql your installing the entire LAMP stack.


i added databases with authenticated users to this thing literally in less than 5 mins. its the only way to go

Thanks for your prompt reply and for the helpful clue!  I just realized that I do have a MySQL Administrator GUI, and that it is indeed easier to manage users and their access to databases using it than going through the mysql command line.

---

