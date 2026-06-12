---
title: "Python MySQLdb Problem"
date: 2007-02-07
forum: Programming Talk
---

### Post by darrenm on 2007-02-07
Hi. Venturing into Python a little bit and I'm trying to write a script that pulls some info from a MySQL database and runs an SSH command using these results.

The code at the moment is:
```

import MySQLdb

def sqlMeat(Company, Column, Table):
        Con = MySQLdb.Connect(host="server", port=3306, user="darrenm", passwd="password", db="adb")
        Cursor = Con.cursor()
        sql = "select " + Column + " from " + Table + " where CompanyRef = '" + Company + "'"
        Cursor.execute(sql)
        Results = Cursor.fetchall()
        Con.close()
        return Results

def getCompanyNames():
        Con = MySQLdb.Connect(host="server", port=3306, user="darrenm", passwd="password", db="adb")
        Cursor = Con.cursor()
        sql = "select CompanyRef from adb"
        Cursor.execute(sql)
        Results = Cursor.fetchall()
        Con.close()
        return Results

def Connect(IP, Rpw, TsIP, Port):
        Command = string.join("ssh -lroot " + IP + " -L*:" + Port + ":" + TsIP + ":3389")
        print Command

CompanyList = getCompanyNames()

i=0
while i < len(CompanyList):
        Company = CompanyList[i]
        Port = 3390
        Connect(sqlMeat(Company, "RouterExternalIP", "locations"), sqlMeat(Company, "RootPassword", "table"), sqlMeat(Company, "TermSrvIP", "table"), Port)
        Port = Port + 1
        i=i+1

```

Its meant to execute and SSH to lots of servers, one after the other with a port forward across SSH, incrementing one every time.

When I execute it I get this:
```
Traceback (most recent call last):
  File "pyssh.py", line 33, in <module>
    Connect(sqlMeat(Company, "RouterExternalIP", "locations"), sqlMeat(Company, "RootPassword", "table"), sqlMeat(Company, "TermSrvIP", "table"), Port)
  File "pyssh.py", line 7, in sqlMeat
    sql = "select " + Column + " from " + Table + " where CompanyRef = '" + Company + "'"
TypeError: cannot concatenate 'str' and 'tuple' objects

```
So it seems I can't construct the SQL statement using the parameters passed to the function? Do I need to convert them to a string before I use them? How can I convert a tuple to a string?
Thanks!

---

### Post by darrenm on 2007-02-07
Hello :)

---

### Post by darrenm on 2007-02-07
Sorted. Had to copy the local variables around and do a string convert. I'm sure there are much easier ways though. The script is now:

```
import MySQLdb
import string
import os
import re

def sqlMeat(Company, Column, Table):
        Con = MySQLdb.Connect(host="server", port=3306, user="darrenm", passwd="password", db="adb")
        Cursor = Con.cursor()
        realCompany = Company[0]
        sql = "select " + Column + " from " + Table + " where CompanyRef = '" + realCompany + "'"
        Cursor.execute(sql)
        Results = Cursor.fetchall()
        Con.close()
        return Results

def getCompanyNames():
        Con = MySQLdb.Connect(host="server", port=3306, user="darrenm", passwd="password", db="dba")
        Cursor = Con.cursor()
        sql = "select CompanyRef from table"
        Cursor.execute(sql)
        Results = Cursor.fetchall()
        Con.close()
        return Results

def Connect(IP, TsIP, Port):
        realIP = IP[0][0]
        realTsIP = TsIP[0][0]
        realPort = str(Port)
        print "IP=" + realIP # For testing
        print "TSIP=" + realTsIP # and again
        print "Port=" + realPort # and again
        Command = "/usr/bin/ssh -lroot " + realIP + " -L*:" + realPort + ":" + realTsIP + ":3389"
        os.popen4(Command)

CompanyList = getCompanyNames()

i=0
Port=3390
while i < len(CompanyList):
        Company = CompanyList[i]
        Connect(sqlMeat(Company, "RouterExternalIP", "locations"), sqlMeat(Company, "TermSrvIP", "table"), Port)
        i=i+1
        Port += 1

```

---

### Post by dwblas on 2007-02-08
You don't have to use SQL.  I like Metakit for this kind of thing.  There are also simple databases like the gdbm type.  The only thing to look out for is if they allow duplicate keys, that is 2 separate records that have the same key, but it doesn't look like that would be a problem here.  Check out databases here for more info
[http://www.python-eggs.org/](http://www.python-eggs.org/)

---

### Post by darrenm on 2007-02-08
Hi, thanks for the tip. Unforturnately the MySQL db is not administered by me and is updated via a PHP front end etc so its a definite need here for me. :)

---

### Post by dwblas on 2007-02-08
Then I would stay with things the way you have them.  All of that is necessary AFAIK.  SQL is a powerful db/language which also means very verbose.  Personally I prefer to put everything into one string as you have and then execute or whatever.  It allows for variables to be included, is more straight forward, and allows for comments to placed where necessary to explain why this object with the non-descriptive name was placed in the string here.

---

### Post by dwblas on 2007-02-08
I came across this today.  I haven't tried it.
> sqlcc is a Python SQL Command Composer It make you composing sql commands without quote & composing strings. You can working in totally Python style, never embed SQL command in string, again.[http://cheeseshop.python.org/pypi/sqlcc/0.2](http://cheeseshop.python.org/pypi/sqlcc/0.2)

---

### Post by darrenm on 2007-02-08
Hmm interesting, will look into that thanks.

---

