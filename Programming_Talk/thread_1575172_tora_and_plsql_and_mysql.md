---
title: "tora and pl/sql and mysql"
date: 2010-09-15
forum: Programming Talk
---

### Post by axyelp on 2010-09-15
my basic requirement is - i want to run pl/sql queries. dbms doesn't matter as long as its available on 10.04

for now, i'm using tora, and whenever i connect it to my 'mysql' database, it shows me this error:
**The tool PL/SQL Editor doesn't support the current database**

and then as the error goes, i cannot see the pl/sql editor or debugger as shown in the documentation! there's no reference to this error anywhere!

it shows the same error even if i use 'root' as user and 'mysql' as database!

what is it i need to do to get it running?

---

### Post by arubislander on 2010-09-15
According to [Wikipedia]("http://en.wikipedia.org/wiki/PL/SQL"):

> PL/SQL is available in Oracle Database (since version 7), TimesTen in-memory database (since version 11.2.1), IBM DB2 (since version 9.7)

So it seems like you are out of luck, as mysql is not in that list.

---

