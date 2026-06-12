---
title: "[SOLVED] mysql help"
date: 2008-05-23
forum: Programming Talk
---

### Post by orlox on 2008-05-23
I hav a couple of questions of mysql, about some select statements...

First..

If i have a table that has a foreign key (for example, a Work table that has a reference to a Client table) how can I perform a select over elements of the work Table using a where clause that checkes for fields of the Client table. For example something like:

Select * from Work where Client.name='Peter';

That should return the elements of the work table that have clients whose name is Peter.

Any help??

---

### Post by Zugzwang on 2008-05-23
You need to perform a select statement over two tables, like:
```

Select * from Work, Client where Client.name='Peter' and Client.ID = Work.ClientID;

```

Replace the "*" by what you actually need.

---

### Post by Mickeysofine1972 on 2008-05-23
> **orlox said:**
> I hav a couple of questions of mysql, about some select statements...

First..

If i have a table that has a foreign key (for example, a Work table that has a reference to a Client table) how can I perform a select over elements of the work Table using a where clause that checkes for fields of the Client table. For example something like:

Select * from Work where Client.name='Peter';

That should return the elements of the work table that have clients whose name is Peter.

Any help??

You could also do this:


```
SELECT * FROM Work JOIN Client ON Work.ID=Client.ID WHERE Client.name='Peter';
```

Mike

---

### Post by orlox on 2008-05-23
Found the solution:

```
select * from Work LEFT JOIN Client ON Work.idClient=Client.idClient WHERE Client.name='Peter';
```

---

