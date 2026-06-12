---
title: "cannot get python-mysql to display server version"
date: 2011-02-18
forum: Programming Talk
---

### Post by brucezepplin on 2011-02-18
Hi guys, I'm learning how to use mysql with python, and have tried the following simple python script:

----------------------------------------------

#server_version.py - retrieve and display database server version

import MySQLdb
conn = MySQLdb.connect (host = "localhost",
                           user = "testuser",
                           passwd = "testpass",
                           db = "test")
cursor = conn.cursor ()
cursor.execute ("SELECT VERSION()")
row = cursor.fetchone ()
print "server version:", row[0]
cursor.close ()
conn.close ()

-----------------------------------------------------
and when I run the script I get this:

arron@arron-laptop:~/Python$ python server_version.py
Traceback (most recent call last):
  File "server_version.py", line 7, in <module>
    db = "test")
  File "/usr/local/lib/python2.6/dist-packages/MySQL_python-1.2.3-py2.6-linux-i686.egg/MySQLdb/__init__.py", line 81, in Connect
    return Connection(*args, **kwargs)
  File "/usr/local/lib/python2.6/dist-packages/MySQL_python-1.2.3-py2.6-linux-i686.egg/MySQLdb/connections.py", line 187, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
_mysql_exceptions.OperationalError: (1045, "Access denied for user 'testuser'@'localhost' (using password: YES)")

but I do not get the server version. Why is this?

also I new here, could someone point me in the direction to wrap my code up so it looks nice and.........codey

Thanks!

---

### Post by MadCow108 on 2011-02-18
the error says access denied.
are you using the correct username and password?

can you login when doing this in the terminal:
```
mysql -h localhost -u testuser -p
```

---

### Post by brucezepplin on 2011-02-18
yes and I get this error code:


ERROR 1045 (28000): Access denied for user 'testuser'@'localhost' (using password: YES)


but I am using the password that I use to go into sudo, so I take it there must be a different password, one I am not aware of....

---

### Post by Some Penguin on 2011-02-18
mysql accounts != linux user accounts

Separate users, separate passwords.

---

