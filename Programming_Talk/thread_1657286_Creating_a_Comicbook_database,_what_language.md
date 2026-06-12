---
title: "Creating a Comicbook database, what language?"
date: 2011-01-01
forum: Programming Talk
---

### Post by EienTatsu on 2011-01-01
I want to start developing an application to keep track of all the comic books I own and want. I want to make a database to keep track of all the information but was wondering what language I should use. I'm not new to programming but I'm pretty new to databases so any help would be appreciated.

---

### Post by worksofcraft on 2011-01-01
> **EienTatsu said:**
> I want to start developing an application to keep track of all the comic books I own and want. I want to make a database to keep track of all the information but was wondering what language I should use. I'm not new to programming but I'm pretty new to databases so any help would be appreciated.

My choice would be to use MySql because it comes with Linux and Windows too and you can access your data-base over the web.

---

### Post by EienTatsu on 2011-01-01
> **worksofcraft said:**
> My choice would be to use MySql because it comes with Linux and Windows too and you can access your data-base over the web.
Can I then write a java app or something to interface with the database. Or would I write an interface in MySQL

---

### Post by worksofcraft on 2011-01-01
> **EienTatsu said:**
> Can I then write a java app or something to interface with the database. Or would I write an interface in MySQL

I only did intreface in PhP but I would think Java be even better :)

---

### Post by EienTatsu on 2011-01-01
> **worksofcraft said:**
> I only did intreface in PhP but I would think Java be even better :)

Okay thanks then I'll go do that then.

---

### Post by worksofcraft on 2011-01-01
> **EienTatsu said:**
> Okay thanks then I'll go do that then.

Well wait see what other say... but meanwhile have a go at setting up LAMP (Linux/Apache/MySql/PhP) stack  :)

oh btw on Windows it is called WAMP stack ;)

---

### Post by EienTatsu on 2011-01-01
> **worksofcraft said:**
> Well wait see what other say... but meanwhile have a go at setting up LAMP (Linux/Apache/MySql/PhP) stack  :)

oh btw on Windows it is called WAMP stack ;)

Thanks, I already have LAMP setup I just need to forward some more ports

---

### Post by kalaharix on 2011-01-01
Happy New Year to all.

Much as I love mySQL, I would suggest you look at SQLite3. Runs on Linux and Windows (with file compatibility).

For someone new to databases, it is easier to nail down because it is file based rather than server based like mySQL.

If you pop the database file in a Dropbox folder then you can read it from anywhere more easily than remote access of a mySQL database.

mySQL is truly mult-user. SQLite can be simultaneously read by many but can only be updated by one user at a time. By the sounds of it, this should not be a problem for you.

---

### Post by EienTatsu on 2011-01-01
> **kalaharix said:**
> Happy New Year to all.

Much as I love mySQL, I would suggest you look at SQLite3. Runs on Linux and Windows (with file compatibility).

For someone new to databases, it is easier to nail down because it is file based rather than server based like mySQL.

If you pop the database file in a Dropbox folder then you can read it from anywhere more easily than remote access of a mySQL database.

mySQL is truly mult-user. SQLite can be simultaneously read by many but can only be updated by one user at a time. By the sounds of it, this should not be a problem for you.If I ever wanted to make a remote app to access the information from another computer would SQLite still work?

---

### Post by kalaharix on 2011-01-01
As long as you are the only user (or more correctly the only updater) then Dropbox works fine.

Your local app and remote app will both use a local copy of the data file. Dropbox automatically keeps the local datafile and remote datafile equivalent.

Depending on how many changed files you have in your Dropbox directory, the computer will take say 10sec to a minute to synchronise when you switch on.

I use this method a lot (frontended with Gambas) going from home to work.

---

### Post by kalaharix on 2011-01-01
As long as you are the only user (or more correctly the only updater) then Dropbox works fine.

Your local app and remote app will both use a local copy of the data file. Dropbox automatically keeps the local datafile and remote datafile equivalent.

Depending on how many changed files you have in your Dropbox directory, the computer will take say 10sec to a minute to synchronise when you switch on.

I use this method a lot (frontended with Gambas) going from home to work.

---

### Post by kalaharix on 2011-01-01
oops. Sorry for double post.

The other advantage is that with mySQL, the remote server must be switched on. With SQLite/Dropbox its all in the cloud.

---

### Post by Lootbox on 2011-01-01
I would check out the MySQLdb module for Python ([download here](http://sourceforge.net/projects/mysql-python/), [tutorial here](http://mysql-python.sourceforge.net/MySQLdb.html)). It's easy to use and if you're familiar with Python, it'll probably quicker to get it up and running than in Java. Here's a short example:

```
#!/usr/bin/python

import sys, MySQLdb

try:
    conn = MySQLdb.connect(host="localhost", user="username", passwd="pass", db="database_name")
except MySQLdb.Error, e:
    print "Error %d: %s" % (e.args[0], e.args[1])
    sys.exit(1)

cursor = conn.cursor()
cursor.execute("SELECT * FROM comicbooks ORDER BY date")
rows = cursor.fetchall()

for row in rows:
    # process each entry (named "row") here

cursor.close()
conn.close()
```

---

### Post by EienTatsu on 2011-01-03
> **Lootbox said:**
> I would check out the MySQLdb module for Python ([download here](http://sourceforge.net/projects/mysql-python/), [tutorial here](http://mysql-python.sourceforge.net/MySQLdb.html)). It's easy to use and if you're familiar with Python, it'll probably quicker to get it up and running than in Java. Here's a short example:

```
#!/usr/bin/python

import sys, MySQLdb

try:
    conn = MySQLdb.connect(host="localhost", user="username", passwd="pass", db="database_name")
except MySQLdb.Error, e:
    print "Error %d: %s" % (e.args[0], e.args[1])
    sys.exit(1)

cursor = conn.cursor()
cursor.execute("SELECT * FROM comicbooks ORDER BY date")
rows = cursor.fetchall()

for row in rows:
    # process each entry (named "row") here

cursor.close()
conn.close()
```
Thanks

---

