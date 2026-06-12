---
title: "Python install script error"
date: 2012-09-14
forum: Programming Talk
---

### Post by Zoica on 2012-09-14
Hello everyone!

Im a new member here, user of Ubuntu 10.04.2 (i know.. old version) ... and im having a problem with compiling some .py script for a program.
When i type $ python /flamenco_install/python/Flamenco.py
I get this error:


Traceback (most recent call last):
  File "/var/www/flamenco_install/python/Flamenco.py", line 3, in <module>
    from FrankenMatrix import *
  File "/var/www/flamenco_install/python/FrankenMatrix.py", line 3, in <module>
    from app import *
  File "/var/www/flamenco_install/python/app.py", line 5, in <module>
    import MySQLdb, metadb, store, logging
  File "/var/www/flamenco_install/python/MySQLdb/__init__.py", line 27, in <module>
    import _mysql
ImportError: libmysqlclient.so.10: cannot open shared object file: No such file or directory

Can you please help me out if you've been in a similar situation?

Thanks!!!

---

### Post by oldfred on 2012-09-14
Welcome to the forums.

Moved to your own thread in the programming sub forum as you were in an old solved thread that most users that might be able to help would not look at since it was solved.

Were there instructions on how to run the installs. Not sure what permissions may be required to install the mySQL server or if you already have it installed that may be an issue.

---

