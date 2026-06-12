---
title: "[SOLVED] Java PreparedStatement"
date: 2008-12-09
forum: Programming Talk
---

### Post by cl333r on 2008-12-09
Hi folks,
I'm getting an error about invalid SQL when doing an update using a java.sql.PreparedStatement.update(str):
```

UPDATE banners_table SET filename = ? , time_added = ? , time_start = ? WHERE id=1

```
> 
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '? , time_added = ? , time_start = ?
...

Am I doing something wrong here or I can't update multiple fields using a prepared statement?

---

### Post by cl333r on 2008-12-09
My bad, I was misusing the prepStat.executeUpdate() method. It must be without arguments.

---

