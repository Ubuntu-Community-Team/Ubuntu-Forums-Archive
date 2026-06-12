---
title: "Simply MySQL question"
date: 2007-01-08
forum: Programming Talk
---

### Post by kj1h234lkj1234 on 2007-01-08
In the past, I've had to insert a row into a database, then use the row ID of the newly-inserted row in another query.

In Access, if I recall, you could do something like this:

```
INSERT INTO `blah` (id, comment) VALUES('', 'blahblah');
```

Then to get the id of the row I just inserted, it was something like:

```
SELECT @@identity FROM `blah`
```(or something like that)

Anyone have any idea what that's called, or how to do it in MySQL?

Thanks

---

### Post by Wim Sturkenboom on 2007-01-08
check the mysql manual for last_insert_id()
from the manual:
```
mysql> SELECT LAST_INSERT_ID();
        -> 195

```

---

### Post by kj1h234lkj1234 on 2007-01-08
Awesome, thanks a lot!

Apparently LAST_INSERT_ID() and @@IDENTITY and exactly the same thing.

*slaps self* :rolleyes:

---

