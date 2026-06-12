---
title: "SQL: primary key vs index vs unique?"
date: 2012-01-23
forum: Programming Talk
---

### Post by anon0 on 2012-01-23
What's the difference between primary key and index, and are they always unique?

I asked how I can implement a check against redundant user names before an insertion. One person said I could do something like
```
$q = mysql_query(' SELEC * FROM $table WHERE username= "johnsmith" ');
If ( mysql_num_rows($q) == 0){
//insertion 
}
```
Another person said this is not optimal because it requires two calls. Instead, he said I should have made the table "username -> INDEX, UNIQUE" to prevent double entry.

By the way, how do you make a column "INDEX, UNIQUE" by SQL query?

---

### Post by Bachstelze on 2012-01-23
```
ALTER TABLE foo ADD UNIQUE (username)
```

[http://dev.mysql.com/doc/refman/5.5/en/alter-table-examples.html](http://dev.mysql.com/doc/refman/5.5/en/alter-table-examples.html)

*EDIT:* An INDEX need not be unique. A UNIQUE may be NULL (and if it is NULL, it is permitted to have more than one row with a NULL value). A PRIMARY KEY is a UNIQUE which is not NULL, and there can be only one PRIMARY KEY in a table.

---

