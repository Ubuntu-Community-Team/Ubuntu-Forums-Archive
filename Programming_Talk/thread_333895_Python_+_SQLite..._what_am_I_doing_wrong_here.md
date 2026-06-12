---
title: "Python + SQLite... what am I doing wrong here?"
date: 2007-01-08
forum: Programming Talk
---

### Post by tribaal on 2007-01-08
Hi guys!

Just started using SQLite for a Python project of mine, and I must say I'm quite impressed with this little database!

However, I keep running into what seems to be a string conversion problem, no matter how simple or complicated my code is... Could some of you have a quick look at my code please? I'm pretty sure it's a dumb programming error (like forgetting semicolons), but I can't find it...

I've installed sqlite with a simple "sudo aptitude install python-sqlite"

Here's the code:

```

import sqlite
connection = sqlite.connect('test.db')
cursor = connection.cursor()

cursor.execute('create table test (num smallint primary key, name varchar(50), email varchar(50))')

name = "Tux"
email = "ilove@herring.org"

cursor.execute('insert into test values(null, ?,?)' , (name,email))


```

Looks pretty straightforward huh?
However I get a nasty "TypeError: not all arguments converted during string formatting" error when I run this (when I do the insert statement, everything works before that, save for typos).

Any ideas?

Thank you so much folks!

- trib'

---

### Post by tribaal on 2007-01-08
EDIT: THis doesn't work because installing "python-sqlite" from the repos will install pysqlite 1.x, what you really want is to install pysqlite 2.x: "sudo aptitude install python-pysqlite2"

Ok I understand my mistake here:
The point is to replace "?"'s by "%s"'s, as for some reason the question marks don't seem to work.

Hope this helps someone...

- trib'

---

