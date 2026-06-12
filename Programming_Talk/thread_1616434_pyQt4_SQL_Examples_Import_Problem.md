---
title: "pyQt4 SQL Examples Import Problem"
date: 2010-11-08
forum: Programming Talk
---

### Post by igb on 2010-11-08
I am starting to develop a program using SQLite and qt4. Trying out the examples that come with py-qt4 I am having a problem with one of the modules.


```
Python 2.6.6 (r266:84292, Sep 15 2010, 16:22:56) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from PyQt4 import QtCore, QtGui, QtSql
>>> import connection
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named connection
>>> 
```

So which module do I need to install for "connection". Searching on Google hasn't helped.

Ian.

---

### Post by spjackson on 2010-11-08
> **igb said:**
> I am starting to develop a program using SQLite and qt4. Trying out the examples that come with py-qt4 I am having a problem with one of the modules.

So which module do I need to install for "connection". Searching on Google hasn't helped.

The connection in the examples refers to connection.py in the examples directory.

---

### Post by igb on 2010-11-08
Doh! Thank you very much.

Ian.

---

