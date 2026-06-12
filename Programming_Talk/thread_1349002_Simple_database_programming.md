---
title: "Simple database programming"
date: 2009-12-07
forum: Programming Talk
---

### Post by raphaelmsx on 2009-12-07
Hi people,

Which language and tools can I use on linux to make a simple database program for my media collection (CDs, DVDs, etc...)?

My goal is to make a console-only application, accessible via local console, telnet, and dumb terminal connected to RS-232 serial port. 

The client application then would have menu options to search the database for specific records (cd title, author, music, etc...), and also edit/include records...

But, it would be cool if after that is complete, the application would have provisions if I decide to go retrocomputing and make a GUI client application on an Amiga, MS-DOS or whatever, to access (and edit/include) the database on the linux server.

It should be as simple as possible, not bloated, doesn't need web access or that type of stuff...

It should also be not so difficult for me to develop, since I'm an infrastructure guy, not a developer. Right now I have basic C knowledge, I can write and compile simple programs, and that's all for the moment, but I want to learn more.

Thank you!

---

### Post by A_Fiachra on 2009-12-08
Why reinvent the wheel -- a basic schema in any relational database will do the trick.  MySQL is popular and has a native Linux flavor.

If you feel so inclined, you can add some prefab queries to an appropriate language like bash, Perl, Python, Java .. etc.

---

### Post by slumbergod on 2009-12-08
It'd be really easy to do in python for the command line. A simple DB wouldn't even need to necessarily import DB libraries since the data structures are really easy to use already.

If you really insist on doing it with C I'd have to agree with the other post...don't reinvent the wheel.

So it really comes down to which language you want to use.

---

### Post by OgreProgrammer on 2009-12-09
Since you are using karmic...

sudo apt-get install quickly

and then type quickly tutorial ubuntu-project

Do that project. It teaches gtk and couchdb. It should be all you need.. and its easy!

---

### Post by Can+~ on 2009-12-09
> **A_Fiachra said:**
> Why reinvent the wheel -- a basic schema in any relational database will do the trick.  MySQL is popular and has a native Linux flavor.

I'd say that even SQLite can do the trick.

[PHP]#!/usr/bin/env python

import sqlite3
import os

# Creates /home/<username>/Desktop/sample.db
location = os.path.join(os.getenv("HOME"), "Desktop", "sample.db")

# Connect to database
conn = sqlite3.connect(location)
curs = conn.cursor()

# Create table and fill it
curs.execute("CREATE TABLE media (id INT, name STR, type STR)")

curs.execute("""INSERT INTO media VALUES
               (1, 'Pearl Jam - Yield', 'music')""")

# Close it
conn.commit()
curs.close()[/PHP]

As easy as it gets... Now that I come to think it, a spreadsheet could do this too.

---

### Post by raphaelmsx on 2009-12-09
Thanks everyone for the answers.

I am not trying to  reinvent the wheel, I just wanted some similar to 80's dbase/clipper running on MS-DOS, but on present day Linux. :)

I will try everything you guys said, if I run into trouble I will post something. ;)

---

### Post by shadylookin on 2009-12-09
I would consider mysql it's popular and easy. Also an xml file might be able to do what you need.

---

### Post by SledgeHammer_999 on 2009-12-10
+1 for sqlite(just one *.c file to compile with your program).

---

### Post by stevescripts on 2009-12-10
and yet another vote for sqlite ;)

Steve

---

### Post by phrostbyte on 2009-12-10
Python and SQLlite (you all need to know a little SQL)

---

