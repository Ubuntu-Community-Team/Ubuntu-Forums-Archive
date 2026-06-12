---
title: "mysql won't run"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by thelugnut on 2008-05-05
I am using 8.04 dis.

I had been using MySQL previous to this upgrade, but it will not run now. 

I get the following error:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I don't know what this means and therefore what to do about it.

Any help, please?

---

### Post by fahadsadah on 2008-05-05
Do you have a MySQL **server** running?
If not, then that is the origin of the problem. Specify a host to connect to with -h

---

### Post by jboy012000 on 2008-05-05
[http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_.html](http://www.linuxforums.org/forum/servers/41668-mysql-problems-_-solved-_.html)

Hi,

Go to the link above and scroll down a few I think that this will help you out.

Cheers

---

### Post by thelugnut on 2008-05-05
My sincere thanks to fahadsadah and jboy012000.

That resolved my problem.

---

