---
title: "How do I create a global object variable in Python?"
date: 2007-11-30
forum: Programming Talk
---

### Post by tc101 on 2007-11-30
How do I create a global object variable in Python?  I am from the VB and may be using the wrong terminology, but I'll explain what I am trying to do.

I create a connection and cursor for a database with this code:

conn = MySQLdb.connect (host = "localhost",
                                     user = "root",
                                     passwd = "",
                                     db = "WebCrawlerDB")
cursor = conn.cursor ()

I would like to do this within a def, and then access the conn and cursor in other defs.  I would like to create global variables for conn and cursor to do this. I tried

conn=object
cursor=object 

but this doesn't work

---

### Post by Quikee on 2007-11-30
> **tc101 said:**
> How do I create a global object variable in Python?  I am from the VB and may be using the wrong terminology, but I'll explain what I am trying to do.

I create a connection and cursor for a database with this code:

conn = MySQLdb.connect (host = "localhost",
                                     user = "root",
                                     passwd = "",
                                     db = "WebCrawlerDB")
cursor = conn.cursor ()

I would like to do this within a def, and then access the conn and cursor in other defs.  I would like to create global variables for conn and cursor to do this. I tried

conn=object
cursor=object 

but this doesn't work

Why don't you just create a class.. something like:

```

class MyDatabaseConnection(object):
	def __init__(self, host, user, passwd, database):
		self.connection = MySQLdb.connect (host, user, password, database)
		self.cursor = conn.cursor()

dbConnection = DatabaseConnection("localhost", "root", "", "WebCrawlerDB")

dbConnection.connection #do something with connection
dbConnection.cursor #do something with cursor

```

Or even better .. do everything database related in this class. ;)

---

### Post by tc101 on 2007-11-30
That seems like a good way to do it.  Thanks for your help.  

I am still curious about the syntax to create a simple global object variable in python.  To create a global integer variable I just do

amt1=0

Is there similar simple syntax for a global object variable?

---

### Post by Quikee on 2007-11-30
> **tc101 said:**
> That seems like a good way to do it.  Thanks for your help.  

I am still curious about the syntax to create a simple global object variable in python.  To create a global integer variable I just do

amt1=0

Is there similar simple syntax for a global object variable?

yes you can do something similar.. but in defs (functions) you have to explicitly say that you are referring to global variable.

Example:
```

globalVariable = 1
globalVariable2 = 1

def test():
	globalVariable = 2

def test2():
	global globalVariable2
	globalVariable2 = 2

test()
print globalVariable

test2()
print globalVariable2


```

In test() the globalVariable was actually a local variable, because I did not explicitly say it is global. ;)

---

