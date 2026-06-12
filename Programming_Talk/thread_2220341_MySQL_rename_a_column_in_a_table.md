---
title: "MySQL rename a column in a table"
date: 2014-04-27
forum: Programming Talk
---

### Post by cp43tcW on 2014-04-27
Hello, I am having trouble renaming a column in a table. I tried both:

```
ALTER TABLE table_name RENAME COLUMN old_name to new_name;
```

and

```
EXEC sp_rename 'TableName.OldName', 'NewName', 'COLUMN'
```

Both give errors.

---

### Post by The Cog on 2014-04-27
After a quick google, it looks like you have to use something like this:

alter table tablename change oldname newname varchar(10);

So you have to re-define the column type as well as the name.

It may help if you posted the error message rather than just saying "give errors" next time. The more info you can give people looking at your problem the better,

---

### Post by cp43tcW on 2014-04-27
It worked. Thank you. I'll post the exact error messages next time.

---

### Post by tgalati4 on 2014-04-27
Cartoons help mysql administration:  [http://xkcd.com/327/](http://xkcd.com/327/)

---

