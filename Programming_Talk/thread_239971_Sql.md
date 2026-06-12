---
title: "Sql"
date: 2006-08-20
forum: Programming Talk
---

### Post by 008325 on 2006-08-20
i have a table

Table user
========
username   : Apple
join day   :2006-10-1
========

join date = current day

now the problem is 

how can i select the username that join day 
is between year 2005 to year 2007 ?

thx a lot

---

### Post by cwaldbieser on 2006-08-20
> **008325 said:**
> i have a table

Table user
========
username   : Apple
join day   :2006-10-1
========

join date = current day

now the problem is 

how can i select the username that join day 
is between year 2005 to year 2007 ?

thx a lot

If you want to select all the user names that joined in a certain date range, the exact syntax may vary a bit depending on the database you are using, but I think it should be something like:

```

select username from user where [join day] between '1/1/2005 00:00:00' and '12/31/2007 23:59:59'

```

---

### Post by ifokkema on 2006-08-22
> **cwaldbieser said:**
> If you want to select all the user names that joined in a certain date range, the exact syntax may vary a bit depending on the database you are using, but I think it should be something like:

```

select username from user where [join day] between '1/1/2005 00:00:00' and '12/31/2007 23:59:59'

```

I guess you could even do
```

SELECT username FROM user WHERE LEFT(join_day, 4) >= 2005 AND LEFT(join_day, 4) <= 2007;
```
Possibly more cross platform, but that's just a guess.

---

