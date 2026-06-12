---
title: "MYSQL/JDBC driver installation issue"
date: 2007-06-18
forum: Programming Talk
---

### Post by afbase on 2007-06-18
in CLI, i try installing the mysql JDBC driver like so.

```
 sudo apt-get install libmysql-java 
```

this is what terminal returns.

> Reading package lists... Done
Building dependency tree... Done
Package libmysql-java is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmysql-java has no installation candidate


Any ideas of what is going on here? or is there another way to install mysql JDBC if i already have the jar file (mysql-connector version version 3.0.17) downloaded from the MYSQL website?

---

### Post by afbase on 2007-06-18
I have this file location 
```
/usr/share/Java6u1/lib
```

I figured I try mapping my setup from my windows' java configuration for Mysql JDBC where the JDBC driver is located 
```
C:\Program Files\Java\java1.6\lib\ext\mysql-connector-java-3.0.17-ga\mysql-connector-java-3.0.17-ga-bin.jar
```

like so:

```
/usr/share/Java6u1/lib/ext/mysql-connector-java-3.0.17-ga/mysql-connector-java-3.0.17-ga-bin.jar
```
it didn't work.  I just deleted the part i added.  Any help would be much appreciated!

---

### Post by afbase on 2007-06-19
Hey can someone help me!!!????

---

