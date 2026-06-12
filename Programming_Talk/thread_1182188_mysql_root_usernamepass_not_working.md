---
title: "mysql root username/pass not working?"
date: 2009-06-08
forum: Programming Talk
---

### Post by mackerman on 2009-06-08
I am attempting to set up a LAMP server on Ubuntu 9.04 Desktop.

I followed some tutorials and have installed PHP & Apache successfully.  WHen I go to login to mysql, I get: 
'mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)'

I have tried uninstalling with the --purge option (sudo apt-get remove --purge mysql-xxxx)

I reinstalled using a blank password for the root user and I still cannot login.  I tried using the old root password that I set up in the initial install and this does not work either.

'mysql -u root -p
Enter Password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)'

Any advice?

---

### Post by Mirge on 2009-06-08
[http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)

---

### Post by mackerman on 2009-06-08
My Solution:  Turns out there was no 'root' user created?
I followed these steps:
```
/etc/init.d/mysql stop
mysqld_safe --skip-grant-tables
mysql -u root mysql
mysql> INSERT INTO user (Host,User,Password) VALUES('%','root',PASSWORD('desiredPassword'));
flush privileges;
exit;
```

Restart sql server (kill process running in other terminal 'ctrl+c')
```
/etc/init.d/mysql restart
```
Upon completion, I tried to login and got: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' error.

To fix:
Create the directory if it is not there:
```
sudo mkdir /var/run/mysqld/
```

touch the file to create it
```
sudo touch /var/run/mysqld/mysqld.sock
```

change the ownership of the folder and socket to the mysql user
```
sudo chown mysql /var/run/mysqld/
sudo chown mysql /var/run/mysqld/mysqld.sock
```

start the mysql server
```
sudo mysqld
```

---

