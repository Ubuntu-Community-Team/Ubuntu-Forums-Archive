---
title: "MySQL SELECT IN"
date: 2012-04-20
forum: Programming Talk
---

### Post by ShareBuntu on 2012-04-20
I've seen this question asked: [http://stackoverflow.com/questions/400712/how-to-do-equivalent-of-limit-distinct](http://stackoverflow.com/questions/400712/how-to-do-equivalent-of-limit-distinct)

I wonder, is it possible to convert this query into something compatible with earlier versions of MySQL (i.e., versions that can't do SELECT IN):

```
select * from table where client_id in(select distinct client_id from table order by client_id limit 5)
```

---

### Post by mehaga on 2012-04-20
No idea, but I guess you'll get a much better response if you ask at mysql forum or stackoverflow.com.

---

### Post by The Cog on 2012-04-21
maybe something like:
> create temporary table tt1 (select distinct client_id from table order by client_id limit 5)
select * from table join tt1 on table.client_id = tt1.client_id
drop table tt1
I seem to remember doing something like that in the past.

---

