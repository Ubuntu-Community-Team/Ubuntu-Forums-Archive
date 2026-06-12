---
title: "SQL - INSERT row number from a ordered select into field"
date: 2008-09-11
forum: Programming Talk
---

### Post by mikeym on 2008-09-11
Hi,

I'm looking to make a field to order a mySQL table by 2 different criteria.

I have a table like this:

```

id   	  image   	  name   	  date   	  page   	  number
296 	clabear000001.jpg 	clabear 	2008-02-28 15:09:40 	/Trip10.htm 	0
590 	clabear000002.jpg 	clabear 	2008-05-28 14:02:12 	/Trip24.htm 	0
591 	clabear000003.jpg 	clabear 	2008-05-28 14:02:47 	/Trip24.htm 	0
592 	clabear000006.jpg 	clabear 	2008-05-28 14:04:25 	/Trip24.htm 	0
593 	clabear000004.jpg 	clabear 	2008-05-28 14:04:25 	/Trip24.htm 	0
343 	daniel000020.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	0
342 	daniel000019.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	0
341 	daniel000021.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	0
340 	daniel000022.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	0
344 	daniel000038.jpg 	daniel 	2008-04-10 11:19:35 	/Trip20.htm 	0
356 	mikey000421.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	0
357 	mikey000420.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	0
358 	mikey000419.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	0
359 	mikey000418.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	0
360 	mikey000417.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	0

```

And I would like to insert a value into the number field that for each image belonging to specific name (eg daniel) orders it by date and inserts its position starting from 1 for each person.

So I would get:

```

id   	  image   	  name   	  date   	  page   	  number
296 	clabear000001.jpg 	clabear 	2008-02-28 15:09:40 	/Trip10.htm 	1
590 	clabear000002.jpg 	clabear 	2008-05-28 14:02:12 	/Trip24.htm 	2
591 	clabear000003.jpg 	clabear 	2008-05-28 14:02:47 	/Trip24.htm 	3
592 	clabear000006.jpg 	clabear 	2008-05-28 14:04:25 	/Trip24.htm 	4
593 	clabear000004.jpg 	clabear 	2008-05-28 14:04:25 	/Trip24.htm 	5
343 	daniel000020.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	1
342 	daniel000019.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	2
341 	daniel000021.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	3
340 	daniel000022.jpg 	daniel 	2008-04-10 11:18:51 	/Trip20.htm 	4
344 	daniel000038.jpg 	daniel 	2008-04-10 11:19:35 	/Trip20.htm 	5
356 	mikey000421.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	1
357 	mikey000420.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	2
358 	mikey000419.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	3
359 	mikey000418.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	4
360 	mikey000417.jpg 	mikey 	2008-04-13 09:20:49 	/Trip21.htm 	5

```

I only want to do this for entries before 2008-09-11 00:00:00 (however this doesn't matter too much because I don't have many images after this and I can sort tham by hand).

Thanks for your time.

---

### Post by mikeym on 2008-09-11
Sorry about this being so off topic, but I know the ubuntu community are a cleaver bunch so hopefully you can help.

---

### Post by Zugzwang on 2008-09-11
> **mikeym said:**
> Sorry about this being so off topic, but I know the ubuntu community are a cleaver bunch so hopefully you can help.

It's certainly not off-topic, but it is certainly not a typical usage case of pure SQL (or MySQL's dialect), so there won't be many people here capable of doing that. I guess many here would use a script making repeated SQL queries/updates for this task.

My Idea would be like this (warning! Just a description, not actual code):
```

Update number from mytable a where number=(
  select counter from (
    select name, counter where name startswith stripnumber(a.name) order by date) 
  where name=a.name
)

```

...using two recursive queries and some special column counting through the entries. Don't know if that's actually possible.

---

### Post by mikeym on 2008-09-11
Thanks. i had a wack at it using SQL and only succeded in insering a bunch of blank records, so I used PHP which the database is being accessed by to script the changes.

---

### Post by Tony Flury on 2008-09-11
Bear in mind that the table itself has no oredring to it - your database might store the rows in the order they are inserted/updated but that is not guaranteed by the SQL standard. Any ordering is provided by selection of the data - i.e. by the ORDER BY clause.

If you don't supply an ORDER BY clause on a SELECT then the order you get is strictly undefined (it might be predictable but.....).

As far as i can tell what you actually want to do is order by person (so clabear's rows come before daniel) and then by date for that person, and the number you mention is just a short hand for the date effectively - and would be broken should you ever insert another record for a person with a date in the middle of the range you have.

So what you actually need is a fairly simple select : 

```

SELECT * FROM table ORDER BY name, date ; 

```

If you think you need the number for something else - let us know - there might be another way of doing what you want without updating your table.

---

