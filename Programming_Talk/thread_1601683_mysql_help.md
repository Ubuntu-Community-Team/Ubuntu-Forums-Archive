---
title: "mysql help"
date: 2010-10-20
forum: Programming Talk
---

### Post by c2tarun on 2010-10-20
hi friends
i just installed mysql server by the command "sudo apt-get install mysql-server"
now i dont know how to open it.
can anyone please help me with this and if possible please tell me any guide or reference material for c programming with my sql
thanx

---

### Post by lykeion on 2010-10-20
I think mysqld is started at bootup by default in Ubuntu.
Manually you can start it with:
```
sudo service mysql start
```
To create databases/tables etc you can login with:
```
mysql -u root -p
```(and enter the password you selected at installation)
Parameters and manual for mysql:
```
man mysql
```
If you need a GUI application for MySQL administration, install this:
```
sudo apt-get install mysql-admin
```
This page is good for some general help/info about MySQL (you could skip the PHP part and scroll down to the MySQL info):
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Regarding accessing MySQL databases in C I'm not sure since I don't do any C programming. Google search got me some resources that might be helpful:
[http://dev.mysql.com/doc/refman/5.1/en/c.html](http://dev.mysql.com/doc/refman/5.1/en/c.html)
[http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html](http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html)
[http://www.kitebird.com/mysql-book/ch06-2ed.pdf](http://www.kitebird.com/mysql-book/ch06-2ed.pdf)

Hope this helps...

---

### Post by Zymus on 2010-10-20
Also, it's best to create your own  user(that way you don't lock yourself out of your database and have to reinstall it). TO do that, type in the following commands:

```

mysql -u root -p
<enter password>
create user 'username'@'localhost';
exit/quit(i can't remember which, i'm not on my main machine)
mysql -u <username> -p<password>
```

ANd you should be good to go.

---

### Post by c2tarun on 2010-10-20
> **lykeion said:**
> I think mysqld is started at bootup by default in Ubuntu.
Manually you can start it with:
```
sudo service mysql start
```To create databases/tables etc you can login with:
```
mysql -u root -p
```(and enter the password you selected at installation)
Parameters and manual for mysql:
```
man mysql
```If you need a GUI application for MySQL administration, install this:
```
sudo apt-get install mysql-admin
```This page is good for some general help/info about MySQL (you could skip the PHP part and scroll down to the MySQL info):
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Regarding accessing MySQL databases in C I'm not sure since I don't do any C programming. Google search got me some resources that might be helpful:
[http://dev.mysql.com/doc/refman/5.1/en/c.html](http://dev.mysql.com/doc/refman/5.1/en/c.html)
[http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html](http://www.cyberciti.biz/tips/linux-unix-connect-mysql-c-api-program.html)
[http://www.kitebird.com/mysql-book/ch06-2ed.pdf](http://www.kitebird.com/mysql-book/ch06-2ed.pdf)

Hope this helps...

> **Zymus said:**
> Also, it's best to create your own  user(that way you don't lock yourself out of your database and have to reinstall it). TO do that, type in the following commands:

```

mysql -u root -p
<enter password>
create user 'username'@'localhost';
exit/quit(i can't remember which, i'm not on my main machine)
mysql -u <username> -p<password>
```ANd you should be good to go.



thanks a lot guys. the links posted by you are really helpful
now i m marking this thread solved.

---

