---
title: "MySQL giving Error 28000, Access Denied ...(using password: YES)"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-23
Hello all,

I have installed mysql using instructions from: 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> 
**Note:**  If you have already set a password for the mysql root, you will need to use: 
mysql -u root -p(Did you forget the mysql-root password?  See [MysqlPasswordReset]("https://help.ubuntu.com/community/MysqlPasswordReset").) 
But when I follow this up using terminal:
```

glenn@acer:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
glenn@acer:~$ 

```Why is it giving me that error when I have already set the password?

---

### Post by Senior_Buckethead on 2012-05-24
Oh come on people..someone has to know the answer...!!

---

### Post by agillator on 2012-05-24
There are a number (large) of possibilities. First, try the obvious. Try logging in without a password. If that works, then IMMEDIATELY set a password for root. If it doesn't, then make sure you are entering the password EXACTLY as you set it. Be careful of special characters. Also try using your hostname, i.e. mysql -h xxxxx -u root -p. You show in your initial message that you are having mysql request your password. If you are trying to enter your password on the command line (mysql -u root -pxxxxxxx) make sure there is NOT a space between the -p and the password. If none of these help, and they may not for various reasons, then follow the instructions you noted for replacing a lost password.

---

### Post by Senior_Buckethead on 2012-05-24
```

glenn@acer:~$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 54
Server version: 5.5.22-0ubuntu1 (Ubuntu)

Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

```

Is this being logged in. I didn't have to set a password, but would one be remembered?

---

### Post by agillator on 2012-05-25
Yes, that is logged in. However, it looks like you are logged in as a guest with limited or no privileges. When logged in that way, try the command 'use mysql' (switch to the mysql database). If it won't let you then you are not root. So quit, and try running 'mysql -u root' and see what that does.

---

### Post by Senior_Buckethead on 2012-05-25
Thanks for the reply.
when i  typed use mysql, I got:
```

mysql> use mysql
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'
mysql>

```So I tried logging in with mysql -u root, and got:
```

glenn@acer:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
glenn@acer:~$ 

```So what does that mean? I can't log in as root? It doesn't have my password stored?

---

### Post by agillator on 2012-05-25
It means two things. First, I was right that you were logged in as a guest with no privileges. In the second case we now know for sure that there IS a password for root, we just don't know what it is. Probably the result of a mistype when you were initially setting up. 

So, your best bet at this point is to follow the instructions you mentioned earlier for resetting the root password. Of course another option is to remove the mysql installation and reinstall it. That really is not very hard to do with the package manager.

---

### Post by Senior_Buckethead on 2012-05-26
Ok for the benefit of anyone else who reads this, I followed the instructions from:
[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
First, I stopped the mysql daemon:
```

sudo /etc/init.d/mysql stop

```then I restarted the mysql daemon process using the --skip-grant-tables option:
```

sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &

```I then restart mysql client:
```

mysql -u root

```I then used this command from the mysql prompt to be able to change password:
```

FLUSH PRIVILEGES;

```I now reset password with:
```

SET PASSWORD FOR root@'localhost' = PASSWORD('xxxxxxxx');

```where xxxxxxxx is my password.
The instructions now tell me that since I have a root account, I should use this command to be able to connect from anywhere:
```

UPDATE mysql.user SET Password=PASSWORD('newpwd') WHERE User='root';

```Once you get a successful message, flush privileges:
```

FLUSH PRIVILEGES;

```Then stop and restart the mysql daemon:
```

sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start

```I then log into mysql with the following command:
```

glenn@acer:~$ mysql -u root -p

```when it should ask you for a password. Once entered, you should be logged into mysql as root:
```

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 49
Server version: 5.5.22-0ubuntu1 (Ubuntu)
Copyright (c) 2000, 2011, Oracle and/or its affiliates. All rights reserved.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql>

```
and testing, I again enter
```

glenn@acer:~$ mysql -u root -p
Enter password: 

```
And I log into mysql.

Have I missed anything important out?

---

### Post by agillator on 2012-05-26
I don't have mysql installed on this computer (I'm on the road at the moment) so I can't duplicate your commands, however in the command where you are setting the password, root@'localhost' should be 'root'@'localhost' (put the root in single quotes). I'll see what I can do to check the rest and get back to you.

---

### Post by agillator on 2012-05-26
OK, I installed mysql and went through your procedures except for two things: I put the root in single quotes in the set password command and I only changed the password once. You showed two commands SET PASSWORD . . . and UPDATE mysql.user . . . that do the same thing - both change the password for the root user on localhost. Unnecessary, use one command or the other. So, with those two modifications my changing of the password went without a hitch. 

So, are you still having trouble? If so, in all honesty the easiest thing to do might well be to remove mysql and reinstall it being very careful in entering the root password during installation. Use something easy to begin with, no special characters, etc. Once you have it set up and you can log in as root you can always change the password to something more secure.

So, sudo apt-get purge mysql-server and then sudo apt-get install mysql-server, assuming you used apt-get to install mysql-server in the first place.

---

### Post by Senior_Buckethead on 2012-06-04
Yes. Solution was to reinstall mysql.

---

