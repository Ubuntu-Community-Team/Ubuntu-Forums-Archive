---
title: "Cannot connect to local mysql server after recent update"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2012-11-07
There has been a recent update of mysql and after that I can no longer connect to my local mysql server. Always get this error

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I have no problem connecting before. Desperately in need of help. Thanks.

OS is Ubuntu 12.04.

---

### Post by CharlesA on 2012-11-07
Run this and see what it says:
```
service mysqld status
```

---

### Post by monkeybrain2012 on 2012-11-07
> **CharlesA said:**
> Run this and see what it says:
```
service mysqld status
```

It says

mysqld: unrecognized service


EDITED:The tag should be Ubuntu rather than lubuntu, can a mod please change it? Thanks.

---

### Post by steeldriver on 2012-11-07
I think the service name is actually mysql not mysqld (even though the process itself is /usr/sbin/mysqld):

```
$ service mysql status
mysql start/running, process 21932

$ ps -ef | grep mysql
mysql    21932     1  0 Nov06 ?        00:00:26 /usr/sbin/mysqld
```

---

### Post by CharlesA on 2012-11-07
Fixed the title.

It looks like the command should actually be:

```
service mysql status
```

---

### Post by monkeybrain2012 on 2012-11-07
I don't know what happens but apparently I couldn't start mysql with "sudo /etc/init.d/mysql start" but somehow "sudo service mysql start" works and now I can log in.

This wasn't the case before the update.

Now I checked that var/log/mysql.log and /var/log/mysql.err and the 
directory /var/log/mysql are all empty, how am I supposed to check for errors if something happens again?


Thanks for the help.

---

### Post by monkeybrain2012 on 2012-11-07
For some strange reason it turns out that in Debian/Ubuntu the mysq log entries are in /var/log/syslog instead of /var/log/mysql.log and /var/log/mysql.err as one would obviously think.

---

