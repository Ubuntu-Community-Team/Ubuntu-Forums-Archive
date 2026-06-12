---
title: "Can't login to Mysql server, the results are as follows"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by the_ntq on 2015-01-07
xxxxxxxx@yyyyyyyyyyy-zzzzzzzz :/$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by Holger_Gehrke on 2015-01-07
Is the mysqld server-process running ?
Try the command
```

pgrep mysqld

```
This should give a number, the process id of the daemon. It should be the same number as in the file /var/run/mysqld/mysql.pid.
Or it could be that you've configured mysql to only listen on the tcp/ip port and not on the named pipe. If that's the case, try adding the options "-h localhost --protocoll=TCP -p 3306"

---

### Post by Habitual on 2015-01-08
> **Holger_Gehrke said:**
> Is the mysqld server-process running ?
Try the command
```

pgrep mysqld

```
This should give a number, the process id of the daemon. It should be the same number as in the file /var/run/mysqld/mysql.pid.
Or it could be that you've configured mysql to only listen on the tcp/ip port and not on the named pipe. If that's the case, try adding the options "-h localhost --protocoll=TCP -p 3306"

or... (don't we LOVE Linux?)

```
telnet localhost 3306
```

---

