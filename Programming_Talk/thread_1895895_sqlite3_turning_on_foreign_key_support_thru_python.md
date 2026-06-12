---
title: "sqlite3: turning on foreign key support thru python"
date: 2011-12-15
forum: Programming Talk
---

### Post by memilanuk on 2011-12-15
I'm setting up an sqlite3 database to use as a base for some programming stuff I want to work on.  Currently using python 2.7, which appears to have a new enough version of sqlite (just barely) to support foreign keys.

As I understand things, sqlite by default has foreign keys turned off, unless specifically compiled otherwise or until you turn on foreign keys using 'pragma foreign_keys=ON'.  And it needs to be turned on for each connection too.

So... just putzing around using the python interactive shell...

```
>>>import sqlite3
>>>sqlite3.sqlite_version
'3.6.21'
>>>conn = sqlite3.connect('contacts.db')
>>>conn.execute('pragma foreign_keys=ON')
<sqlite3.Cursor object at 0x00B61860>
>>>conn.execute('pragma foreign_keys')
<sqlite3.Cursor object at 0x00B6F020>
>>>
```

It appears I am able to successfully import sqlite3, its of a recent enough version to support foreign keys (> 3.6.19), I connected it to an existing database 'contacts.db', and when I execute the pragma statement to turn on foreign key support it returns a cursor object.  Similarly, when I send a pragma statement to query the status of foreign key support, it returns a cursor object.

Now for the stupid question(s):  

How do I tell if it succeeded?  How do I use that cursor object returned by the pragma query to tell if its a '1' (on) or a '0' (off)?

---

### Post by memilanuk on 2011-12-16
Got the answer from another source; figured I'd pass it on here for the benefit of anyone using the search engine in the future ;)

Need to iterate over the cursor object returned by the pragma statement like so:

```

rows = conn.execute('pragma foreign_keys')
for row in rows:
    print row
```

which should return a tuple of (1,) or (0,) depending on whether foreign key support is enabled or not.

FWIW, the statement to turn on foreign keys:

```

conn.execute('pragma foreign_keys=ON')

``` 

also returns a cursor object, but one that is *not* iterable.

---

