---
title: "pysqlite smart search"
date: 2009-02-23
forum: Programming Talk
---

### Post by KLIA on 2009-02-23
Hey guys;

I am trying to develop a tiny program using python to search inside sq-lite database with file extension is .db in which the program will ask users to enter their search query and base on that it will retrieve the results But

I need the program to have some smartness in search mechanism in which the program will guess that the user is looking for this key word in the database.

So far i came up with this but the search ain't smart, i have to write the full key word in order to retrieve specific information.

```

from pysqlite2 import dbapi2 as sqlite3

connection = sqlite3.connect('Photos.db')
memoryConnection = sqlite3.connect(':memory:')
cursor = connection.cursor()
prompt = 'Enter your search query?\n'
keyword = raw_input(prompt)
if cursor.execute('SELECT * FROM photos WHERE Tag LIKE ?',[keyword]):
print cursor.fetchall()
else:
cursor.execute('SELECT * FROM photos WHERE Date LIKE ?', [keyword])
print cursor.fetchall()

```

Any ideas and
thanks in advance

---

### Post by ajackson on 2009-02-23
My use of LIKE in SQL is a bit rusty but if I remember right you can do something like
```
LIKE zxz%
```
Which will include all values starting with zxz, so stick a % from and back of your search term should give you that partial match you are after (as I said I'm a bit rusty with the LIKE syntax so I might be wrong).

---

### Post by unutbu on 2009-02-23
% is to sql as .* is to regexp.
So if you put a % on both sides of the keyword, then will match anything that contains the keyword string.

E.g.:
```
LIKE %zxz%
```

---

