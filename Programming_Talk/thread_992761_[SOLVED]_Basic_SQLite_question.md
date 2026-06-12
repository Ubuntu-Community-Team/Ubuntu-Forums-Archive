---
title: "[SOLVED] Basic SQLite question"
date: 2008-11-25
forum: Programming Talk
---

### Post by lovinglinux on 2008-11-25
I need some help with sqlite3 syntax.

I'm writing a few shell scripts integrated with a sqlite database. I need to get the values from a column and copy to another column in the same entry. Is it possible?

For example:

```
sqlite3 ~/mydatabase.sqlite "update mytable set column_to_be_updated='**[COLOR="Red"]????[/COLOR]**' where filtered_column='${VARIABLE}'"
```

What I want is to get the "[COLOR="Red"]**????**[/COLOR]" value from another column without using a variable.

If this is not possible, how could I retrieve data for each entry row separately? I have multiple entries with the same filtered ${VARIABLE}, so when I replace [COLOR="Red"]**????**[/COLOR] with another variable, it grabs the column value from all entries.

---

### Post by CptPicard on 2008-11-25
```


update table set column_to_update=column_to_get_value_from where..


```

---

### Post by lovinglinux on 2008-11-25
> **CptPicard said:**
> ```


update table set column_to_update=column_to_get_value_from where..


```

Thank you very much! 

I feel kind of stupid tho :mrgreen:

---

