---
title: "Mysql tables are read only??"
date: 2007-12-12
forum: Programming Talk
---

### Post by sdowney717 on 2007-12-12
Here is what happens, I log into mysql, try to update a table and it is read only. 
Infact all DB's and all tables are read only.
Any ideas?

scott@scott-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 32
Server version: 5.0.45-Debian_1ubuntu3-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> use books5
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> update usertable set myuser='help';
ERROR 1036 (HY000): Table 'usertable' is read only
mysql> GRANT ALL ON *.* TO 'root'@'localhost' IDENTIFIED BY 'New';
Query OK, 0 rows affected (0.09 sec)

mysql> update usertable set myuser='help';
ERROR 1036 (HY000): Table 'usertable' is read only
mysql>

---

### Post by sdowney717 on 2007-12-12
figured it out sort of.
The database folder has to be owned by MySql Server and not root etc....

I discovered this by importing into a new database a sql backup
Now updates work etc....

But how would you change the ownership to mysql-server?
It is not in the list.


mysql> create database grr;
Query OK, 1 row affected (0.02 sec)

then do this:
scott@scott-desktop:~$ mysql -u root -p grr<backup.sql
Enter password: 

data is entered into grr

then this:

mysql> select * from usertable;
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
| Id | MyName  | Myuser   | password | Priveliges            | TS                  | UserDate            |
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
|  1 |         | New      | WD      | p        | 2006-01-23 13:14:44 | 2006-01-23 13:14:46 | 
|  2 | student | student  | BFFPPXC  | v                | 2006-01-25 11:25:07 | 2006-01-25 11:25:07 | 
|  3 |         | 5thgrade |         | v          | 2006-02-06 13:25:24 | 2006-02-06 13:25:38 | 
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
3 rows in set (0.00 sec)

mysql> update usertable set myuser='6thgrade' where myuser='5thgrade';
Query OK, 1 row affected (0.04 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from usertable;
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
| Id | MyName  | Myuser   | password | Priveliges            | TS                  | UserDate            |
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
|  1 |         | New      | WD      | p        | 2006-01-23 13:14:44 | 2006-01-23 13:14:46 | 
|  2 | student | student  | BFFPPXC  | v                | 2006-01-25 11:25:07 | 2006-01-25 11:25:07 | 
|  3 |         | 6thgrade |         | v          | 2007-12-12 18:39:46 | 2006-02-06 13:25:38 | 
+----+---------+----------+----------+-----------------------+---------------------+---------------------+
3 rows in set (0.00 sec)

mysql>

---

### Post by sdowney717 on 2007-12-12
if you look, 
books5 is owned by root
grr is owned by mysql server

---

### Post by sdowney717 on 2007-12-15
also you have to set the iptable to ok the use of port 3306 for mysql

[https://help.ubuntu.com/community/IptablesHowTo#head-5e8d1517266cc39cfc52db70758a9ce9646ec5fc](https://help.ubuntu.com/community/IptablesHowTo#head-5e8d1517266cc39cfc52db70758a9ce9646ec5fc)
[http://www.cyberciti.biz/tips/linux-iptables-18-allow-mysql-server-incoming-request.html](http://www.cyberciti.biz/tips/linux-iptables-18-allow-mysql-server-incoming-request.html)

sudo iptables -A INPUT -p tcp --dport 3306 -j ACCEPT

and you have to allow users to connect remotely thru grant syntax
[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

and you have to edit my.cnf 
normally mysql is only listening to localhost, so comment out bind address in
etc/mysql/my.cnf

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address		= 127.0.0.1


still would like to know how to change ownership to mysql server for a database folder.

---

### Post by maryalexandraagner on 2011-12-31
In order to fix the read-only table problem, you need to 

1 - shut down your mysql server

2 - use the chown command to change the owner and group of the files in your database to the mysql user 
 Example:  chown  -R mysql:mysql database_name
(Note:  this version changes both the owner and the group)

3 - restart your mysql server

You may need to be root to make the chown command happen.

---

### Post by richardelima on 2012-01-07
how can i grant access to the table to actual user, being they owned by nobody:root, without having to chown the folder? (because i sync daily bases witha windows db wich changes the owner to the actual user.

---

