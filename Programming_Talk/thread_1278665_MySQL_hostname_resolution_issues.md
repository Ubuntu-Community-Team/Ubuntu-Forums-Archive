---
title: "MySQL hostname resolution issues"
date: 2009-09-29
forum: Programming Talk
---

### Post by mdavidn on 2009-09-29
I'm working with some legacy (i.e. very bad) PHP code that makes connections to multiple MySQL servers, each on port 3306. In my local dev environment, I'm binding separate instances of MySQL to different loopback interfaces. (e.g. 127.1.0.1, 127.1.0.2, etc)

Everything works fine on the networking side. I can resolve the name, and I can open a connection...
```
$ resolveip rajah-slave
IP address of rajah-slave is 127.1.0.2
```
```
$ nmap rajah-slave -p 3306

Starting Nmap 4.76 ( http://nmap.org ) at 2009-09-29 16:47 PDT
Interesting ports on rajah-slave (127.1.0.2):
PORT     STATE SERVICE
3306/tcp open  mysql

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
```
```
$ netstat -ln | grep 3306
tcp        0      0 127.1.2.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.1.0.3:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.1.0.2:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
```

... but MySQL chokes when resolving the hostname.

```
$ mysql -h rajah-slave
ERROR 2005 (HY000): Unknown MySQL server host 'rajah-slave' (-1)
```
```
$ mysql -h 127.1.0.2
Welcome to the MySQL monitor.  Commands end with ; or \g.

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```
Any guesses as to why this doesn't work? I'm stumped! ](*,)

---

### Post by mdavidn on 2009-09-29
Okay, so hostname resolution in the mysql client dies a painful (and silent) death if *any* line in /etc/hosts is too long.

Problem solved!

---

