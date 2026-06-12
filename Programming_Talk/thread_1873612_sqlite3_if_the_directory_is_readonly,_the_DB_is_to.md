---
title: "sqlite3: if the directory is readonly, the DB is too?"
date: 2011-11-01
forum: Programming Talk
---

### Post by azzamite on 2011-11-01
Hello guys

I'm having a little problem here, I noticed that if the directory in which a sqlite database is stored is read-only I can't modify the database even if I have write permission in the file!

Here is a little example of what I'm doing, first save this as **db.py**:
[PHP]#!/usr/bin/python3
import sqlite3

con = sqlite3.connect("/tmp/dir/test.db")

try: con.execute("create table foo(a integer, o integer, e integer, u integer)")
except: print ("failed to create db... ignoring")

con.execute("insert into foo values (0, -1, -1, -1)")
cur = con.execute("select * from foo")
for i in cur: print(i)

con.commit()[/PHP]

Then execute the following:

```
me:~$ chmod +x ./db.py
me:~$ mkdir /tmp/dir
me:~$ ./db.py 
me:~$ ./db.py 
failed to create db... ignoring
(0, -1, -1, -1)
me:~$ chmod 500 /tmp/dir/
me:~$ ./db.py 
failed to create db... ignoring
(0, -1, -1, -1)
(0, -1, -1, -1)
Traceback (most recent call last):
  File "./db.py", line 11, in <module>
    con.execute("insert into foo values (0, -1, -1, -1)")
sqlite3.OperationalError: unable to open database file
```

As you can see, the error is "unable to open database file", however the select statement succeeded.

So the question is: 
Is it possible to write in the DB even if the directory is readonly?

---

### Post by gsmanners on 2011-11-01
Don't you need like a cursor and another commit and a close in there?

EDIT: I'm looking at [http://docs.python.org/py3k/library/sqlite3.html](http://docs.python.org/py3k/library/sqlite3.html)

---

### Post by MadCow108 on 2011-11-01
strace the process to see whats going wrong:
```
strace -e open ./db.py
open("/tmp/dir/test.db-journal", O_RDWR|O_CREAT, 0644) = -1 EACCES (Permission denied)
```

sqlite3 tries to create a journal file in the directory to provide atomicity.
because there are no write permissions this is not allowed and fails

---

### Post by azzamite on 2011-11-01
Thanks for your help MadCow108, I found a way to prevent the creation of such journal file:

[PHP]con.execute("PRAGMA journal_mode =  OFF")[/PHP]

Now let's see how long it takes to get a corrupted database file :o

Cheers

---

