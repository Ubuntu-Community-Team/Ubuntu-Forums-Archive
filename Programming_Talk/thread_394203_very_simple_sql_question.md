---
title: "very simple sql question"
date: 2007-03-26
forum: Programming Talk
---

### Post by monkeyking on 2007-03-26
I'm a total newbie in mysql.

I have a problem, that in simple terms  can be explained as th following.

I have a table called base.
with the following columns

name, phone, addr.


Now I want a new table with the following columns from the previous,

phone, name.

That is I would like to swap the first two and drop the last. one.

thanks in advance

---

### Post by monkeyking on 2007-03-26
okey I worked it out by myself.

the syntax is quite simple.
```
insert into base2
select phone,name from base;
```

---

### Post by pmasiar on 2007-03-26
You can just "select phone,name from base" - you don't have to create new table to view subset of fields or different order. Why you want to create new table?

---

### Post by Mirrorball on 2007-03-26
And if you don't need the name anymore, you can just drop the field.

---

