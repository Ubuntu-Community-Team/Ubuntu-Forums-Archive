---
title: "Python: MySQL / Database question"
date: 2008-10-13
forum: Programming Talk
---

### Post by lixeno on 2008-10-13
Hello,

i have two files:

[B]
main.py
test.py
[/B]

My question is if there's anyway for test.py to access objects in main.py?

I want to setup a database connection in **main.py** and utilize this connection in **test.py** in order to lower the number of connections.

This is just and example, and there would be at least 10 different files wanting to access the object or being able to interact with the database without starting a new connection

In PHP i would simply create a new connection and it would work for all the files included?

New to python,
Thanks

---

### Post by mike_g on 2008-10-13
> My question is if there's anyway for test.py to access objects in main.py
Yes, you want to import the objects from the other files. Similar to "include" or "require" in PHP. Heres an example from some code I wrote using SQLite, with the main class importing everything from db.py:
```
#! /usr/bin/env python

from db import *

class MainClass:

	def __init__(self):
            ...
```

An this would be db.py:
```
from pysqlite2 import dbapi2 as sqlite

class Database:
    ...
```

---

### Post by mssever on 2008-10-13
More generally, you can access the public (and non-public, under some circumstances) functions, classes, attributes, etc. of one module from another module with no problem. Here's a simple example: ```
#test.py
def connection_function(*args):
    '''Return a database connection object'''
    # do stuff

connection = connection_function(arg1, arg2)

#################

# main.py:
import test

if not test.connection:
    test.connection = test.connection_function(arg1, arg2)

the_connection = test.connection
```

---

### Post by unutbu on 2008-10-13
main.py

[PHP]
#!/usr/bin/env python
import sys
import MySQLdb
import _mysql_exceptions
class DB(object):    
    def __init__(
        self,thehost="xxxx",theuser="xxxx",
        thepasswd="xxxx",thedb="xxxx"):
        print "__init__"
        if not hasattr(DB,'connection'):
            try:
                #
                # This makes a single MysQLdb.connect object which is shared by 
                # every instance of the db.DB class
                #
                DB.connection = MySQLdb.connect(
                    host=thehost,user=theuser,passwd=thepasswd,db=thedb)
                print "Got here"
            except _mysql_exceptions.OperationalError:
                sys.exit('Failed to form a MySQLdb connection')
        self.connection=DB.connection
        self.cursor=DB.connection.cursor
[/PHP]

##########

test.py
[PHP]
#!/usr/bin/env python  
import main
db=main.DB()
#__init__
#Got here

db2=main.DB()   # Notice how the second time you call main.DB(), 'Got here' doesn't print
#__init__

print db.connection
#<_mysql.connection open to 'localhost' at 8224d94>

print db2.connection
#<_mysql.connection open to 'localhost' at 8224d94>

assert(db.connection is db2.connection)   # Since this command does not raise an exception, we know db.connection is literally the same object as db2.connection.

print db.cursor 
#<bound method Connection.cursor of <_mysql.connection open to 'localhost' at 8224d94>> 
[/PHP]

The first time main.DB() is called, a MySQLdb.connect() object is returned. It is also saved as a class attribute, DB.connection.

The second time main.DB() is called, __init__ checks if DB has attribute 'connection', and if so, self.connection is hooked up to the same DB.connection.

This ensures that no matter how many times main.DB() is called, you always get the same connection.

---

### Post by lixeno on 2008-10-13
Ah, awesome.. Thanks for all your help everyone, appreciate it!  :D

---

