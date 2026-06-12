---
title: "JDBC-ODBC Bridge Issues"
date: 2011-07-21
forum: Programming Talk
---

### Post by chinaCat86 on 2011-07-21
I need to connect to an MS Access data source using [oXygen]("http://www.oxygenxml.com/") XML editor. I have had this working on a windows computer last year, however, I am having trouble connecting this on Ubuntu 11.04. It continually returns java.sql.SQLException: null

[img]https://lh5.googleusercontent.com/-bkbSqqZGm58/TidKaKlh7fI/AAAAAAAAABY/UxBbM2ErBkA/temp3.png[/img]


I feel like it is a simple solution, but I am stumped and have spent too much of my work day on this. Has anyone encountered this before, or has any advice to offer?


What I have Done:

**In <oXygen/>**
1. Configured JDBC-ODBC Bridge
[img]https://lh3.googleusercontent.com/-nj4SI0xWBjE/TidJkVMW63I/AAAAAAAAABU/nYcKZ5ppaHM/temp1.png[/img]

2.Configured Connection
[img]https://lh3.googleusercontent.com/-YNSwwm2P8dY/TidJkZjGVCI/AAAAAAAAABQ/UO1CSAPrm9k/temp2.png[/img]

**In Ubuntu 11.04**
1. Added a link to a file-system client based on ssh
```
sshfs -p22 matt@192.168.1.196:/productionFolder /media/productionServer
```
2. Added Microsoft Access Driver to odbcinst.ini
```
$ cat /etc/odbcinst.ini 
[Microsoft Access Driver]
Description =   MDB Tools ODBC drivers
Driver = /usr/lib/libmdbodbc.so.0
Setup = /usr/lib/libmdbodbc.so.0
FileUseage = 1

```
3. Added ODBC connection to odbc.ini[/list]
```
$ cat /etc/odbc.ini 
[production]
Driver  =   Microsoft Access Driver
Description =   Production ODBC Connector
Trace   =   Yes
TraceFile   =   /tmp/odbc.log
Database    =   /media/productionServer/Production/production--00.mdb

```
4. Tested the connection
```
$ isql -v production 
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> quit

```

And Yet, in oXygen It still returns with java.sql.SQLException: null

---

