---
title: "msyql browser"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by 007casper on 2012-06-05
I am having a problem with seting up mysql query browser.  I tried several things, and have been at it several days.  I still cant create a connection.

on the remote server /etc/mysql/my.cnf bind address is set to local network IP.  It is not localhost, nor 127.0.0.1

so, on my local computer I changed /etc/mysql/my.cnf to bind address=0.0.0.0

on the terminal> 
ssh -p 2222 -v -f -N -L 3307:192.168.152.2:3306 user@serverip

then, I open the query browser. 
server hostname: 127.0.0.1
port: 3307
user:root
password: <pass>

then, on the query browser I get > 
Could not connect to host '127.0.0.1'.
MySQL Error Nr. 1130
Host '192.168.152.2' is not allowed to connect to this MySQL server

on the terminal> 
Connection to port 3307 forwarding to 192.168.152.2 port 3306 requested.
debug1: channel 2: new [direct-tcpip]
debug1: Connection to port 3307 forwarding to 192.168.152.2 port 3306 requested.
debug1: channel 3: new [direct-tcpip]
debug1: channel 2: free: direct-tcpip: listening port 3307 for 192.168.152.2 port 3306, connect from 127.0.0.1 port 58429, nchannels 4
debug1: channel 3: free: direct-tcpip: listening port 3307 for 192.168.152.2 port 3306, connect from 127.0.0.1 port 58430, nchannels 3

please, help.  Thank you.

---

### Post by 007casper on 2012-06-05
I wonder if mysql user is the issue
```

mysql> SELECT User, Host, Password FROM mysql.user;
+------------------+-----------------+-------------------------------------------+
| User             | Host            | Password                                  |
+------------------+-----------------+-------------------------------------------+
| root             | localhost       | *924384AFJLFAJ23024379823437LAJADFWOEIR29 |
| root             | mysql           | *924384AFJLFAJ23024379823437LAJADFWOEIR29 |
| root             | 127.0.0.1       | *924384AFJLFAJ23024379823437LAJADFWOEIR29 |
| debian-sys-maint | localhost       | *924384AFJLFAJ23024379823437LAJADFWOEIR29 |
| dbuserfileeee    | 192.168.152.2   | *124384AFJL20CBF7008CF52E986EAJADFWOEIR29 |
+------------------+-----------------+-------------------------------------------+
5 rows in set (0.00 sec)

mysql> SHOW GRANTS FOR 'dbuserfileeee'@'192.168.152.2';
+----------------------------------------------------------------------------------------------------------------------------+
| Grants for dbuserfileeee@192.168.152.2                                                                                   |
+----------------------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'dbuserfileeee'@'192.168.152.2' IDENTIFIED BY PASSWORD '*4A760265DF20CBF7008CF52E986EE59009A3114A' |
| GRANT ALL PRIVILEGES ON `dbname`.* TO 'dbuserfileeee'@'192.168.152.2'                                          |
+----------------------------------------------------------------------------------------------------------------------------+

```

---

### Post by stmiller on 2012-06-05
> Host '192.168.152.2' is not allowed to connect to this MySQL server 

This means there is no row in the user table with a Host value that matches 192.168.152.2 and the user you are trying.

In other words, you are trying to use user 'root', but the table does not have a Host value of 192.168.152.2 for root.

Cheers,

---

