---
title: "simple SQL problem"
date: 2006-07-27
forum: Programming Talk
---

### Post by theconley on 2006-07-27
I want to select the number 1 in it's own row, nothing more.

I can do:

```
SELECT 1 FROM arbitrarytable FETCH FIRST 1 ONLY
```

But I don't want to use an arbitrary table when I shouldn't need to, and for this particalar subquery, I can't use FETCH FIRST 1 ONLY, legally.

Any suggestions?

~Conley

---

### Post by fabiand on 2006-07-27
Hey,

you mean to fetch only the first matching result?

You can try to use the following:
```

SELECT * FROM arbtable WHERE rowx=y LIMIT 1
```

---

### Post by yaaarrrgg on 2006-07-27
select 1?  you can try :

```

SELECT 1

```

:)

---

### Post by LordHunter317 on 2006-07-27
What database?  Some, like Oracle, require a fake table in order to select arbitrary values like that.

***Always specify database.***

---

