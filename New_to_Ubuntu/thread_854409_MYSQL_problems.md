---
title: "MYSQL problems"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ahbb on 2008-07-09
HI there,

Wonder if you could help me pls.

Iv done everything like its sed on this help url.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

But all the other stuff work Apache is running everything but my mysql dont want to start.

This is the error that im getting.

root@ahbb:~# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

Please advice as i need to run urgent a mysql database on that server.

Thanks once again.

Andrew

---

### Post by OffAxis on 2008-07-09
did you input a root user name and password?

```
mysql -u username -p password
```

---

### Post by ahbb on 2008-07-09
Hi,

No i have not, but when i try to do that, cmd it make the user and then when i enter the psw it give me the same error again.

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Andrew

---

### Post by OffAxis on 2008-07-09
If you didn't set a root password then the syntax should be
```
mysql -u root
```
and that should get you to a mysql command prompt.

you can restart the mysql server with 
```
sudo /etc/init.d/mysql restart
```

---

### Post by ahbb on 2008-07-09
hi there,

Even when i try to use that cmd i get the same error.

Do you think i need to uninstaal mysql and reinstall it maybe?

root@ahbb:/# mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

This is really working on my nerves now...

Thanks

Andrew

---

### Post by Cypher on 2008-07-09
Please do the following..
```

ls -l /var/run/mysqld
sudo /etc/init.d/mysql stop
ls -l /var/run/mysqld
sudo /etc/init.d/mysql start
ls -l /var/run/mysqld

```

---

### Post by ahbb on 2008-07-09
hi,

Iv done as you sed and then at the end when you have to start it again.

It give the same error.

I show you everything i did now.

root@ahbb:/# ls -l /var/run/mysqld
total 0
root@ahbb:/# sudo /etc/init.d/mysql stop
Stopping MySQL database server: mysqld.
root@ahbb:/# ls -l /var/run/mysqld
total 0
root@ahbb:/# sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
root@ahbb:/# ls -l /var/run/mysqld
total 0
root@ahbb:/#


Thanks

Andrew

---

### Post by OffAxis on 2008-07-09
did you change the bind-address in the /etc/mysql/my.cnf file?

try changing it back to **localhost **and restart the server.

---

### Post by fatality_uk on 2008-07-09
If memory serves me correctly, that's a permission tables error/bug.
Let me check my notes and ge back to you, but you could do a search in MySql forums for that error code.

---

### Post by fatality_uk on 2008-07-09
Check here to see if this helps
[http://forums.mysql.com/read.php?11,9689,71099#msg-71099](http://forums.mysql.com/read.php?11,9689,71099#msg-71099)

---

### Post by ahbb on 2008-07-10
Hi all,

Thanks for the help, i went to that website and look thru all those ppl's errors that is the same as mine, but iv tried what they sed, but still dont work.

Any advice for me pls?

Im still getting the same error. I cant even start mysql nothing to change or add users nothing.

Thanks

Andrew

---

### Post by virus2 on 2008-09-01
Hi,
iam having this same problem.If you got the solution to it,then pls tell me.
Andrew,
can you tell me how you installed the PHP,Apache AND MYSQL on your machine.I suspect it is the sequence of installation of these apps that matters.
In my case,I first MANUALLY installed Mysql5.0.67 through tar.gz file.After installing it,I started the server and got the mysql prompt as well,but I didnt test or use it after that.
After some days,I installed Apache2.0 and PHP5,both through Adept manager.
After 1 week of installation of Apche and PHP,i tried to start the mysql,but am faced with the issue faced by you.
I also suspect that it has got something to do with my.cnf file in etc/mysql.
Also,in my case.I cannot find any directory in */var/run *with the name of *mysqld*,whereas the my.cnf clearly indicates this path.

Pls do post if you got the solution.

Thanks,
Satish

---

### Post by lakersforce on 2008-10-11
Same problem here

EDIT: Worked after I installed the server :) (mysql-server, not just client)

---

