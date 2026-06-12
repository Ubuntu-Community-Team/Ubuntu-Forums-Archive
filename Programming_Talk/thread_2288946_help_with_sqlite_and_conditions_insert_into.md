---
title: "help with sqlite and conditions insert into"
date: 2015-07-30
forum: Programming Talk
---

### Post by fugu2 on 2015-07-30
I would like to find a way to do a conditional INSERT INTO mytable where specific conditions must be met before the insert actually happens. I can do this in multiple steps, but the process is painfully slow bacuse its making multiple queries to the sqlite engine, where I think it should be able to do thing in a single query.
```

sqlite3 mydb 'CREATE TABLE IF NOT EXISTS mytable(id INTEGER, num INTEGER);'
sqlite3 mydb 'INSERT INTO mytable(id, num) VALUES ("1", "2");'
sqlite3 mydb 'INSERT INTO mytable(id, num) VALUES ("1", "1") WHERE ( id != "1" AND num != "1" );'
sqlite3 mydb 'INSERT INTO mytable(id, num) VALUES ("1", "2") WHERE ( id != "1" AND num != "2" );'
sqlitebrowser mydb

```
can anyone help me out?

---

### Post by trent.josephsen on 2015-07-30
> **fugu2 said:**
> ```
sqlite3 mydb 'INSERT INTO mytable(id, num) VALUES ("1", "1") WHERE ( id != "1" AND num != "1" );'
```

INSERT with WHERE? Is that valid SQL? What does it even do?

More to the point, what is it supposed to do? My SQL is rusty but if you want to conditionally insert, you probably want to wrap the INSERT in an IF.

---

### Post by fugu2 on 2015-07-30
Can you provide an example of how I might wrap an insert statement with an if?

---

### Post by trent.josephsen on 2015-07-31
Sorry, no, sqlite doesn't have IF. Probably because it doesn't support stored procedures. However, this seems to do something sensible:
```
sqlite> CREATE TABLE dogs (id INTEGER PRIMARY KEY, name, shots);
sqlite> INSERT INTO dogs (name, shots)
   ...> SELECT 'Brutus', 'true'
   ...> WHERE NOT EXISTS(SELECT 1 FROM dogs WHERE name='Brutus');
```
Maybe you can adapt that.

---

### Post by fugu2 on 2015-08-08
I finally figured out a solution, which is not exactly what I wanted but it will definitely work. Thank you for your directions they were a great help. This is what I came up with, I had to add the NOT NULL clause to my table but thats ok for what Im doing:
```

sqlite3 mydb 'CREATE TABLE IF NOT EXISTS mytable(id INTEGER NOT NULL, num INTEGER NOT NULL);'
sqlite3 mydb 'INSERT OR IGNORE INTO mytable(id, num) VALUES ( 
CASE 
	WHEN NOT EXISTS(SELECT * FROM mytable WHERE id="1" AND num="2") THEN 
		"1" 
	ELSE 
		NULL 
END, 
CASE 
	WHEN NOT EXISTS(SELECT * FROM mytable WHERE id="1" AND num="2") THEN 
		"2" 
	ELSE 
		NULL 
END);'

```
So basically its like I have a uniqueness to each row, I had trouble explaining what I wanted, and now that I'm finished, I can just show what I was after, lol. I don't like the fact that I have to search twice to see if the table has those entries, but oh well. If anyone knows a better way to do this, or has any suggestions, please let me know. Thank you for all your help.

---

### Post by oldfred on 2015-08-08
If you index on that field and not allow duplicates, it will not let you enter a second value. 

I indexed several fields and I regularly get error messages on duplicates.

---

### Post by fugu2 on 2015-08-10
I was looking for row uniqueness, so these would all be valid entries:
```

INSERT INTO mytable(id, num) VALUES ("1", "1");
INSERT INTO mytable(id, num) VALUES ("1", "2");
INSERT INTO mytable(id, num) VALUES ("1", "3");
INSERT INTO mytable(id, num) VALUES ("2", "1");
INSERT INTO mytable(id, num) VALUES ("2", "2");
INSERT INTO mytable(id, num) VALUES ("2", "3");
INSERT INTO mytable(id, num) VALUES ("3", "1");
INSERT INTO mytable(id, num) VALUES ("3", "2");
INSERT INTO mytable(id, num) VALUES ("3", "3");

```
but I want it to not be able to add a second one; like this should not be added:
```

INSERT INTO mytable(id, num) VALUES ("2", "1");

```
because its already in the table. I'm really just beginning to learn sql so please bear with me.

---

### Post by oldfred on 2015-08-10
Multi-column index?
[https://www.sqlite.org/queryplanner.html](https://www.sqlite.org/queryplanner.html)

---

