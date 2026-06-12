---
title: "Python method creation question"
date: 2010-05-03
forum: Programming Talk
---

### Post by Adrienk on 2010-05-03
I have the following code:

```


import cx_Oracle
from urllib import urlopen

dbconn = cx_Oracle.connect('usr', 'password', '127.0.0.1/XE')
dbconn.autocommit = True
cur = dbconn.cursor()

class close:
    def closeConnection(self):
        try:
            dbconn.close()
        except Exception:
            print Exception
            return False
        finally:
            dbconn.quit()


```I am sure you all know what this does, for those who dosen't its a file that open a data base connection and has a method that closes the connection (when called) assuming no SQL exceptions have been thrown.

My questions are as follows:

1) How can I right the close method better in terms of handeling exceptions?
2) How can I surround the "open a dbconn" in a method (function) - sorry use to java - with out the dbconn in def close() becoming "an undefined variable"?

This file is part of a package that gets imported and thus used to create tables and what not based on user input.
Also how would I call the class close into the other file known as commands in the pakage database commands?

I have been doing:

```


import MakeConnection
from MakeConnection import Connection
from Connection import *



```But if I try to go  close() as it is (see below) I get errors, saying close is a undefined variable?!

```


import MakeConnection
from MakeConnection import Connection
from Connection import *

close()

```


even if I did something like:

```
class close:
    def DBCONN(self):
        dbconn = cx_Oracle.connect('lab8', 'password', '127.0.0.1/XE')
        dbconn.autocommit = True
        cur = dbconn.cursor()
         
    def closeConnection(self, DBCONN):
        try:
            dbconn.close()
        except Exception:
            print Exception
            return False
        finally:
            dbconn.quit()
```

I A) dont think this is right, B) wouldnt know how to call the individual peices of this class and C)dbconn in closeConnection is now "undefined variable"....

I need the database connection to be in a class or method so it can be called into any file containing commands or database manipulations
and I need close in a method or class so that after all the manipulations and what not are done you can just call close

---

### Post by Adrienk on 2010-05-03
Bump edited. Need some help on this matter

---

### Post by Adrienk on 2010-05-03
Bump

---

### Post by trent.josephsen on 2010-05-03
Hmm... smells like homework, but I'll bite.

I have a question.  Why have you written a class solely to close a database connection?  No class is needed there, and having it is merely confusing.  Just call dbconn.close(), with exception handling in-line if need be.

What you probably want to do is pull the connection making and closing code into a module like so:

```
# in Connection.py
def makeConnection(host, user, password):
    dbConn = cx_Oracle.connect(user, password, host)
    return dbConn

def closeConnection(dbConn):
    ok = True
    try:
        dbConn.close()
    except:
        ok = False
    dbConn.quit() # no need for 'finally'; flow falls through anyway
    return ok

```

Then you can use it like so:
```

import Connection
dbConn = Connection.makeConnection('127.0.0.1/XE', 'usr', 'password')
# ... do some stuff ...
if not Connection.closeConnection(dbConn):
    # dbConn.close() failed; perform diagnostics

```

There are several things wrong with your final attempt, but frankly I'm not sure which ones are real mistakes and which are my misinterpretations.  How would you try to use that in client code?  You do know Python is case sensitive, right?

---

### Post by Adrienk on 2010-05-03
This post has been deleted please see the one below

---

### Post by Adrienk on 2010-05-04
> **trent.josephsen said:**
> Hmm... smells like homework, but I'll bite.

I have a question.  Why have you written a class solely to close a database connection?  No class is needed there, and having it is merely confusing.  Just call dbconn.close(), with exception handling in-line if need be.

What you probably want to do is pull the connection making and closing code into a module like so:

```
# in Connection.py
def makeConnection(host, user, pass):
    dbConn = cx_Oracle.connect(user, pass, host)
    return dbConn

def closeConnection(dbConn):
    ok = True
    try:
        dbConn.close()
    except:
        ok = False
    dbConn.quit() # no need for 'finally'; flow falls through anyway
    return ok

```Then you can use it like so:
```

import Connection
dbConn = Connection.makeConnection('127.0.0.1/XE', 'usr', 'password')
# ... do some stuff ...
if not Connection.closeConnection(dbConn):
    # dbConn.close() failed; perform diagnostics

```There are several things wrong with your final attempt, but frankly I'm not sure which ones are real mistakes and which are my misinterpretations.  How would you try to use that in client code?  You do know Python is case sensitive, right?


Not homework - I am done school for the summer, if this was in java then yes it would be....But i know how to do it in java.

your first peice of code throws the following error while compiling:

  File "C:\Users\usr\workspace\src\MakeConnection\Connection.py", line 14
    def makeConnection(host, user, pass):
                                      ^
SyntaxError: invalid syntax

---

### Post by trent.josephsen on 2010-05-04
> **Adrienk said:**
> Not homework - I am done school for the summer, if this was in java then yes it would be....But i know how to do it in java.

your first peice of code throws the following error while compiling:

  File "C:\Users\usr\workspace\src\MakeConnection\Connection.py", line 14
    def makeConnection(host, user, pass):
                                      ^
SyntaxError: invalid syntax

Yeah, forgot "pass" is a Python reserved word.  I didn't try to compile it myself because it's just there to give you the idea.

---

### Post by Adrienk on 2010-05-04
> **trent.josephsen said:**
> Yeah, forgot "pass" is a Python reserved word.  I didn't try to compile it myself because it's just there to give you the idea.

Ya I do, and I got it work kind, I replaced pass with pwsd.

so in my commands.py file I imported the same way you did and called the "method" the same way, but I get the error:

```
 Traceback (most recent call last):
  File "C:\Users\Adam Balan\workspace\src\Commands\Commands.py", line 13, in <module>
    dbConn = Connection.makeConnection('lab8', 'password', '127.0.0.1/EX')
  File "C:\Users\Adam Balan\workspace\src\MakeConnection\Connection.py", line 17, in makeConnection
    dbConn = cx_Oracle.connect(user, pswd, host)
cx_Oracle.DatabaseError: ORA-12514: TNS:listener does not currently know of service requested in connect descriptor
```Now I have a database at that address with those credentials
The issue though that I am having is the error its spitting out....


do you have any idea as to why it won't connect?

I even ```
import cx_Oracle
``` and still get the error...

I think its saying cannot find the location of this  database.....

the code I had before had no issue connecting....(I think....LOL, never really tested it...)

******Had some code backwards - fixed it but still getting the same error******

---

### Post by Adrienk on 2010-05-04
bump

---

### Post by Adrienk on 2010-05-04
bump

---

### Post by trent.josephsen on 2010-05-04
Don't neglect to pass the correct parameters: (host, user, pass) in my version of makeConnection, but (user, pass, host) in cx_Oracle.connect.  And I don't know whether you meant '127.0.0.1/EX' or '127.0.0.1/XE'.

A word of advice:  Bumping your own thread multiple times is perceived as impatient and annoying.  This is a forum; you can't expect instantaneous replies -- most people (myself included) only log on at certain times of day, and posting again won't change that.  At most bump 3 times and never more than once in 24 hours.

---

### Post by Adrienk on 2010-05-05
so Now that I fixed some things

See the following code:

```
'''
Created on May 3, 2010

@author: Adam Balan

this file is used to call the connection file from the pakage make connection to allow for commands to be issued.
all commands are stored as either class or method form to allow for calling in the appdrive pakage.
This file is part of the Commands pakage
'''
import cx_Oracle
from MakeConnection import Connection

dbConn = Connection.makeConnection('lab8', 'password', '127.0.0.1/XE')
dbConn.autocommit = True
cur = dbConn.cursor()
cur.execute("""CREAT TABLE STUDENT (STUDENT_ID) VARCHAR2(30)""" )
cur.close()
if not Connection.closeConnection(dbConn):
    print "Failed to open a connection"
```

and I get the following error:

```
Traceback (most recent call last):
  File "C:\Users\Adam Balan\workspace\src\Commands\Commands.py", line 16, in <module>
    cur.execute("""CREAT TABLE STUDENT (STUDENT_ID) VARCHAR2(30)""" )
cx_Oracle.DatabaseError: ORA-00900: invalid SQL statement
```

I know SQL and that should have worked (also how can I put in NOT NULL?

in java this is so easy but i want to learn to do this in python

---

### Post by trent.josephsen on 2010-05-05
In my experience SQL error messages are among the least helpful on the planet, second only to 500 errors in CGI scripts.  The best advice I can give is to log in to the database directly and try running your statements from a SQL prompt.  How that may be done with Oracle I don't know, my experience mainly being SQLite, MySQL and Informix.

But... you do mean "CREATE" not "CREAT" right?  And forgive my ignorance but is VARCHAR2 actually a type for Oracle?

---

### Post by Adrienk on 2010-05-05
yes VARCHAR2 and VARCHAR are types in oracle.
Um I fixed the issue. but now....now I have a new issue....



In java I can do something like this:

```
    public void delete()
    {
        String delete = JOptionPane.showInputDialog("Please choose the row from HIKE based on the primary key you would like to delete:");
        try
        {
            stmt = conn.createStatement();
            String query = "DELETE FROM HIKE WHERE HIKE_CODE = " + delete;
            results = stmt.executeQuery(query);
        }
        catch (SQLException e)
        {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
```

So in python I tried to do:

```
ShowTables = raw_input("Enter in the table you want to see the information in: ")
cur.execute("""DECRIBE TABLE""" + ShowTables)

```

Which is basically the same thing....
But I get the :

```
  File "C:\Users\Adam Balan\workspace\src\Commands\Commands.py", line 34, in <module>
    cur.execute("""DECRIBE TABLE""" + ShowTables)
cx_Oracle.DatabaseError: ORA-00900: invalid SQL statement
```

How would I do this?

---

