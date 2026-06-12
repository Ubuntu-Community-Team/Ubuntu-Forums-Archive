---
title: "[MySQL] MySQL server start failed!"
date: 2009-11-11
forum: Programming Talk
---

### Post by GarudaReiga on 2009-11-11
Hey folks -

I installed the LAMP stack on my Ubuntu 8.04 LTS. My MySQL server was working at the beginning, however it couldn't start after I configured the Apache2 a little bit.

When I check MySQL if running or not
```
# mysqladmin -u root -p status
```
The output is:
```
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

When I check MySQL status using
```
# /etc/init.d/mysql status
```
The output is:
```
 * MySQL is stopped.
```

So I decided to start my MySQL server
```
# /etc/init.d/mysql start
```
The output is:
```
 * Starting MySQL database server mysqld [fail] 
``` 

Then I check my syslog under /var/log/syslog
```

Nov 11 10:35:29 Garuda mysqld_safe[7806]: started
Nov 11 10:35:29 Garuda mysqld[7809]: 091111 10:35:29  InnoDB: Started; log sequence number 0 43675
Nov 11 10:35:29 Garuda mysqld[7809]: 091111 10:35:29 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
Nov 11 10:35:29 Garuda mysqld_safe[7821]: ended
Nov 11 10:35:44 Garuda /etc/init.d/mysql[7971]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Nov 11 10:35:44 Garuda /etc/init.d/mysql[7971]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Nov 11 10:35:44 Garuda /etc/init.d/mysql[7971]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Nov 11 10:35:44 Garuda /etc/init.d/mysql[7971]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Nov 11 10:35:44 Garuda /etc/init.d/mysql[7971]: 

```


The problem happened to me before, and I can't solve it. I actually reinstall the MySQL and reboot the Ubuntu, which solves the problem. Now, it comes out again pissing me off.:confused:

I know lots of people met the same problem, I couldn't find the graceful solution. Therefore, I think if we can figure out what is the root cause, and what is the final solution on a specific platform(Ubuntu), it might be very helpful for other newbies like me.

Thank you in advance for your suggestions.:p

---

### Post by Can+~ on 2009-11-11
> I installed the LAMP stack on my Ubuntu 8.04 LTS. My MySQL server was working at the beginning, however it couldn't start after I configured the Apache2 **a little bit**.

What did you change?

---

### Post by GarudaReiga on 2009-11-11
I followed the instruction of [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by GarudaReiga on 2009-11-11
> **Can+~ said:**
> What did you change?

I followed the instruction of [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
1) # gedit /etc/apache2/conf.d/fqdn --> Add "ServerName localhost"
2) Set the default site to be /home/user/public_html/
# sudo a2dissite default && sudo a2ensite mysite

Then nothing else.

---

