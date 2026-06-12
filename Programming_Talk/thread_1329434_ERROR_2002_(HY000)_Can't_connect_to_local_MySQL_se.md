---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2009-11-17
forum: Programming Talk
---

### Post by rugger0 on 2009-11-17
I installed 9.10 from scratch then started to fill it in with the packages I need using synaptic. 
I wanted to setup a LAMP and I ended up with no Mysql.

Mysql processes don't start: no results from ps -e | grep mysql
What I get is this error:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

How can I fix this?

thank you in advance

---

### Post by phpmonkey on 2009-11-19
I was getting a similar message, and I realised I had only downloaded mysql-client-5.1 but not mysql-server-5.1 ](*,)

I followed this guide: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) to make sure I didn't do anything else silly in my haste to get LAMP up and running on 9.10!

Just in case it helps someone else... ;)

---

