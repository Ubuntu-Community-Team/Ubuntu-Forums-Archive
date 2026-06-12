---
title: "Installing mySQLdb in Ubuntu"
date: 2012-03-01
forum: Programming Talk
---

### Post by HoneyBadger1 on 2012-03-01
Guys I installed mySQLdb in Ubuntu  with:

```
mycomp@mycomp-desktop:~$ sudo apt-get install python-mysqldb
``` but when I go to the python interpreter and type:
```
>>> import mySQLdb 
```I get:

```
 Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named mySQLdb

```It is installed though, because when I go to:

System > Administration > Synaptic Package Manager and type mysql I can see:

python-mysqldb as installed.


why does it not work?

---

### Post by JDShu on 2012-03-01
[http://www.kitebird.com/articles/pydbapi.html](http://www.kitebird.com/articles/pydbapi.html)

Check the capitalization in your import statement.

---

