---
title: "Databases - need help with creating a schema"
date: 2009-01-01
forum: Programming Talk
---

### Post by Vadi on 2009-01-01
Hi all,

Does anyone have any tips/resources on database scheming? I need to create a DB that will store changing data about applications on a daily basis.

My first idea was to have a table for each app, then inside that for each day, and inside each day for the data of each day - however that was using the data model as data storage itself, which was a no-no. I can't figure out another way for this - a possible idea was to have a table for all apps, and one for all days, but I am unsure how to link them together.

Any help is appreciated.

---

### Post by davec64 on 2009-01-01
First off, sorry but I use MSSQL:(

But what about:

A series of Look up tables i.e.
[INDENT]Applications Table[/INDENT]
[INDENT]Date Table etc[/INDENT]

And then have your data table linked to your look ups by foreign keys, so the data table would have a row for each event you want to record referenced to an Application and a Date etc.

Just a thought!

I might have missed the mark completely though! :D

---

### Post by Vadi on 2009-01-01
Didn't quite get your point, but wouldn't new tables need to be created for new dates?

---

### Post by pp. on 2009-01-01
Let's say you wanted to record the size, the temperature and the colour of each application on a day to day basis.

That'd take exactly one table with exactly five columns:
- application id
- date
- size
- temperature
- colour

---

### Post by Vadi on 2009-01-01
> **pp. said:**
> Let's say you wanted to record the size, the temperature and the colour of each application on a day to day basis.

That'd take exactly one table with exactly five columns:
- application id
- date
- size
- temperature
- colour

I don't see how would that work though. I'd need to know the size of a given application on a given day, temperature of a given app on a given day... this way wouldn't work that I see. Unless I'm missing something completely obvious?

---

### Post by pp. on 2009-01-01
```

Date	        Application	Colour	Size	Temperature
01.01.09	Evolution	pink	XL	45
01.01.09	Calc	        reddish	XXL	20
02.01.09	Evolution	pink	XL	36

```

---

### Post by Vadi on 2009-01-01
Doh, yes, that is a possible solution. The only worry about is that Applications need to be unique - at least I was hoping as such, because performance might be affected when querying by the string. But at least I have a possible base to now stand on. Thanks much!

(rather silly to miss out this idea of me)

---

### Post by pp. on 2009-01-01
If you want to make sure that each application is written exactly the same each time it is mentioned, you'd add a second table containing the application names only. You'd then instruct you database to allow application names in the wide table only if they are present in the narrow one.

---

### Post by mike_g on 2009-01-01
> Doh, yes, that is a possible solution. The only worry about is that Applications need to be unique - at least I was hoping as such, because performance might be affected when querying by the string. But at least I have a possible base to now stand on. Thanks much!
I'd use an indexed application id for the search queries. You could then add the application name as an extra column, or add a separate linked 'application' table storing the name to avoid redundancy.

---

