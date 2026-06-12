---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2017-02-07
forum: New to Ubuntu
---

### Post by divya.bharathi on 2017-02-07
hi,
I'm getting ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
error when I try to start mysql. 
I tried the below methods to reslve this error.But no luck.Please help resolving this problem. I'm using Unbuntu 14.04.
I hv tried to change the password. But unable to do that. 
Then I tried by starting mysql service. It is already running. 
When I try  with command ps -ef | grep mysql, I'm getting the below response. . 


hadoop@hadoopvbox:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
hadoop@hadoopvbox:~$ mysql -u root 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
hadoop@hadoopvbox:~$ sudo mysqladmin password newpassword
[sudo] password for hadoop: 
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
hadoop@hadoopvbox:~$ sudo service mysql start
start: Job is already running: mysql
hadoop@hadoopvbox:~$ sudo service mysqld start
mysqld: unrecognized service
hadoop@hadoopvbox:~$ ps -ef | grep mysql
mysql     1006     1  0 21:44 ?        00:00:00 /usr/sbin/mysqld
hadoop    3329  3167  0 22:00 pts/0    00:00:00 grep --color=auto mysql

---

### Post by sacmo on 2017-02-12
Sounds like a broken configuration or maybe broken install, try 
sudo dpkg-reconfigure mysql-server-5.1 and see if this helps you, if not you might need to remove mysql install and reinstall it and all the packages required.

Good luck, let us know if it works.

---

