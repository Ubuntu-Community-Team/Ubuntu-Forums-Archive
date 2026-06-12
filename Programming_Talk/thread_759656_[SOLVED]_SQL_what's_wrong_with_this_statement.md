---
title: "[SOLVED] SQL: what's wrong with this statement?"
date: 2008-04-19
forum: Programming Talk
---

### Post by x1a4 on 2008-04-19
Hi,

MySQL keeps telling me that the following statement has a syntax error: 
```

select * from `ld_links` where `catid`=10 limit 0,10 order by `title`

```

Can anyone tell me what's wrong with this?

Thank you.

---

### Post by Rinzwind on 2008-04-19
Well... for 1 you miss a semicolon at the end ;)

---

### Post by pmasiar on 2008-04-19
Try this:

[PHP]select * from ld_links where catid=10 limit 10 order by title[/PHP]

Assuming that 
- ld_links is table name
- catid, title are field names in that table

Then, get into habit never use select *, always mention fields. Good habit to have: if you have *, it better should be count(*).

---

### Post by x1a4 on 2008-04-19
Thank you for your prompt replies.  The semicolon is not it as I'm using this query from PHP using the mysql_query() function which frowns on semicolons in its SQL.  

Removing the quotes and the initial value from the LIMIT clause is not it also, plus I need it for proper pagination of results in a PHP script.

---

### Post by stevescripts on 2008-04-19
duh ... a couple of questions...

Why are you using backticks (`) rather than  (') ?

Shouldn't there be a space between 'catid' = 10 ?

I dont consider myself an SQL expert, but I do quite a bit from time to time,
though I only use SQLite anymore.

Keep in mind what pmasiar said about getting in the habit of not
using select *  ... 

Would have been nice to know you were doing this from PHP -
kinda makes my post obsolete (was composing it, while trying
to work)

Hope this helps a bit.

Steve

---

### Post by x1a4 on 2008-04-19
Thank you everyone for your replies.  I figured it out.  The problem was the LIMIT clause which belongs at the end.  The following works now: 
```
select * from `ld_links` where `catid`=10 order by `title` limit 0,10
```

I use backticks because phpMyAdmin uses them and I sometimes use it to generate complex queries for me, and I got into the habit of using them as well.  Plus it saves me from having to escape quotes.  Also, I generally bracket and quote the heck out of everything to avoid any ambigueties {sp?}

---

