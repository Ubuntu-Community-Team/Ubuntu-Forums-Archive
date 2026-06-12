---
title: "problem with python and mysql"
date: 2009-12-20
forum: Programming Talk
---

### Post by Despot Despondency on 2009-12-20
Hi,

I'm trying to learn how to access databases using python but I'm having some problems. I've imported MySQLdb but when I run the command 

```

cxn = MySQLdb.connect(user='root')

```

I get the error

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/MySQLdb/__init__.py", line 74, in Connect
    return Connection(*args, **kwargs)
  File "/var/lib/python-support/python2.5/MySQLdb/connections.py", line 170, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
_mysql_exceptions.OperationalError: (2002, "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)")

```

I've found various suggestions but I don't know which to try. Any suggestions would be appreciated. TAI

---

### Post by Despot Despondency on 2009-12-20
I don't know why this thread say SOLVED but it is not.

---

### Post by The Cog on 2009-12-21
You almost certainly need to supply a passwd parameter as well.
cxn = MySQLdb.connect(user='root', passwd='whatever')

Don't forget to COMMIT any database writes, or you will spend many hours wondering why your data doesn't get written to the database. I've been there, got the t-shirt.

---

