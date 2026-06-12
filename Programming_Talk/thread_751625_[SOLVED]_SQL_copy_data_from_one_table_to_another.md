---
title: "[SOLVED] SQL: copy data from one table to another"
date: 2008-04-10
forum: Programming Talk
---

### Post by x1a4 on 2008-04-10
Hi,

I want to copy the data in fields `id`,`title`,`keywords`,`description` in table `linkdir_cat` to fields `id`,`title`,`kw`,`desc` in table `ld_cat`
My SQL is this:
```

insert into `ld_cat` (`id`,`title`,`kw`,`desc`)
select `id`,`title`,`keywords`,`description`
from `linkdir_cat`

```

The problem is that `id` in both tables has 'auto_increment' set, and I get a 'duplicate entry' error when trying to insert the second row.  When I remove 'auto_increment' from `ld_cat`.`id`, the data copies just fine, but then I can't set 'auto_increment' again.  

How do I copy data from one table to another and still have 'auto_increment' set in the new table?

Thank you.

---

### Post by Can+~ on 2008-04-10
First, let me say that I'm a sql newb, so I may be wrong:

Why don't you exclude the id from the operation? And I guess there are other better commands for that:

[http://www.w3schools.com/Sql/sql_select_into.asp](http://www.w3schools.com/Sql/sql_select_into.asp)

---

### Post by pmasiar on 2008-04-10
do you want autoincrement IDs in both tables the same? or they can be different?

---

### Post by x1a4 on 2008-04-10
> **pmasiar said:**
> do you want autoincrement IDs in both tables the same? or they can be different?

They can be different.  The new table is part of some changes I'm making to the database and script that will access it.  Once I'm done the old tables will be deleted.  But it is important that all the data (including IDs) is exactly the same in the new table as in the old when I first copy the data.

---

### Post by x1a4 on 2008-04-10
> **Can+~ said:**
> Why don't you exclude the id from the operation? 

I just did and it worked.  Thank you.

---

