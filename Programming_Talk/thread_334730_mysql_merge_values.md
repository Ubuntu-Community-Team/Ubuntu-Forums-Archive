---
title: "mysql merge values"
date: 2007-01-09
forum: Programming Talk
---

### Post by tocleora on 2007-01-09
I have a date field that some of the dates have a year of 2007.  I want to change those 2007's to 2006's.  I was thinking something like this:

```
update employees set dateofhire = '2006' & right(dateofhire,6) where dateofhire > curdate()
```

But I'm going to guess that's not the right syntax.  Doing a search for right on mysql.org pulls several different results.  Can anyone give me the proper syntax?  TIA...

---

### Post by marianom on 2007-01-09
I would just add a whole year with dates arithmetic as seen here: [http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html](http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html)

---

### Post by tocleora on 2007-01-09
That'll do! Thanks!

---

