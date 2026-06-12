---
title: "Mysql comma separated &quot;or&quot;"
date: 2006-11-29
forum: Programming Talk
---

### Post by tocleora on 2006-11-29
A coworker said that he saw not too long ago a way to do an sql query instead of like:

select * from table where a = 1 or a = 2 or a = 3

something like:

select * from table where a = (1,2,3)

I have *no* idea how to search for this... Anyone know what he's talking about and can possibly provide some information?  TIA!

---

### Post by geoffm33 on 2006-11-29
I think you are looking for something like

```
select * from table where a in (1, 2, 3, 4, 5);
```

This is from memory so the syntax probably isn't completely correct.

---

### Post by addicted68098 on 2006-11-29
> **geoffm33 said:**
> I think you are looking for something like

```
select * from table where a in (1, 2, 3, 4, 5);
```

This is from memory so the syntax probably isn't completely correct.

That does work, just tried it out now!

The other method doesn't work, it returned error 1064 so it didn't reconize the  = (multiple) thing at all.

---

### Post by jgcamp99 on 2006-11-29
[http://www.w3schools.com/sql/sql_in.asp](http://www.w3schools.com/sql/sql_in.asp)

Example 1

To display the persons with LastName equal to "Hansen" **or** "Pettersen", use the following SQL:

SELECT * FROM Persons
WHERE LastName IN ('Hansen','Pettersen')

Result:
LastName 	FirstName 	Address 	City
Hansen 	Ola 	Timoteivn 10 	Sandnes
Pettersen 	Kari 	Storgt 20 	Stavanger

---

### Post by tocleora on 2006-11-30
Yeah that's it...  Funny, we were thinking it was "out" but out didn't make sense where mysql is normally easy to read, we never thought to try the reverse! :)  thanks!

---

### Post by ohgod on 2006-12-01
I believe the 'select * from tbl where id in (1,2,3,4)' syntax is part of the SQL standard.  At least this method works on M$ Sql Server as well.

---

