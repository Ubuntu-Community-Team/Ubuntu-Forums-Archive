---
title: "[SOLVED] Pysqlite2 Get Last Inserted Row Id"
date: 2008-09-29
forum: Programming Talk
---

### Post by mike_g on 2008-09-29
I want to do this: [http://www.sqlite.org/c3ref/last_insert_rowid.html](http://www.sqlite.org/c3ref/last_insert_rowid.html) with pysqlite. I have been searching around for about half an hour now and I cant seem to find the binding for it. Does one exist? If so what is it?

Cheers.

---

### Post by mike_g on 2008-09-29
Ok, I wrote my own implementation, but I'm not sure if its all that great. Hopefully it should work fine with an auto incrementing id.
```
	def get_last_row_id(self):
		last = None
		for row in self.cursor.execute("SELECT ROWID FROM entry"):
			last = row[0]
		print "Last ID: "+str(last)
		return last 
```

---

### Post by Mindzai on 2008-09-29
EDIT: Sorry didn't read your initial post properly before replying but i'll leave my reply in case it is any use anyway

------------------------------------------------------------------------

Try using the following query:

```
SELECT last_insert_rowid()
```

Though that will not necessarily help you as it only returns the last insert over your whole database. If this is unnaceptable, you could use your approach but you run the risk of unexpected results if there are many inserts in quick succession.

My approach would be to have a table containing 2 fields, table name and last insert id, then add after update triggers for each table thus:

```
CREATE TRIGGER table1_insert AFTER INSERT ON table1 BEGIN
     UPDATE last_inserts
     SET insert_id = last_insert_rowid()
     WHERE table = 'table1';
END;

etc...

```

You can then query this table as necessary. May be overkill for what you need though?

---

### Post by SteelDragon on 2008-09-29
From the [pysqlite documentation]("http://oss.itsystementwicklung.de/download/pysqlite/doc/sqlite3.html"):

> Cursor.lastrowid
    This read-only attribute provides the rowid of the last modified row. It is only set if you issued a INSERT statement using the execute() method. For operations other than INSERT or when executemany() is called, lastrowid is set to None.

So basically, all you need is a cursor object and you can get the last row id easily. Unless you are interested in the rowid of a row not created by the INSERT statement?

---

### Post by mike_g on 2008-09-29
Cool, thanks for the link :) The site looks as if it should be useful.

---

