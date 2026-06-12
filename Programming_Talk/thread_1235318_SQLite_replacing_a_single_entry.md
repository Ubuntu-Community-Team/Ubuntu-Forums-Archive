---
title: "SQLite: replacing a single entry"
date: 2009-08-08
forum: Programming Talk
---

### Post by King_Critter on 2009-08-08
I'm trying to replace a single entry in an SQLite database.

I thought something like this would work:

```
cursor.execute('REPLACE INTO wallpapers (display) VALUES("tiled") WHERE id=5')
```

...but it doesn't work, and [this page]("http://www.sqlite.org/lang_insert.html") is laughing at me.

Help please?

---

### Post by unutbu on 2009-08-09
According to [http://www.sqlite.org/lang_insert.html](http://www.sqlite.org/lang_insert.html), REPLACE is provided for compatibility with MySQL's REPLACE command. 

MySQL's REPLACE does not permit WHERE clauses. The REPLACE command performs a DELETE and then INSERT when "an old row in the table has the same value as a new row for a PRIMARY KEY or a UNIQUE  index". (See [http://dev.mysql.com/doc/refman/5.0/en/replace.html](http://dev.mysql.com/doc/refman/5.0/en/replace.html))

In other words, instead of saying WHERE id=5, I think you would need to setup the table so the id field is a PRIMARY KEY or UNIQUE index, and then try:

```
cursor.execute('REPLACE INTO wallpapers (id,display) VALUES (5,"tiled"))
```

---

### Post by Can+~ on 2009-08-09
How about [UPDATE]("http://www.sqlite.org/lang_update.html")?

```
cursor.execute('UPDATE wallpapers SET display="tiled" WHERE id=5')
```

---

### Post by King_Critter on 2009-08-09
Excellent! UPDATE is exactly what I was looking for. Guess I should RTFM next time before asking questions. :P

unutbu, your suggestion works too, but in this case UPDATE is simpler.

Much thanks to both of you. ^_^

---

