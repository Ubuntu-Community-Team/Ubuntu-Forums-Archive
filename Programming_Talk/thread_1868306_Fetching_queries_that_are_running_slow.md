---
title: "Fetching queries that are running slow"
date: 2011-10-24
forum: Programming Talk
---

### Post by vjohnny8 on 2011-10-24
Hi all,

Is there any tool in Oracle 9i, by which we can fetch queries or database statements that are running slow in the entire database on a weekly basis ?

---

### Post by karlson on 2011-10-24
> **vjohnny8 said:**
> Hi all,

Is there any tool in Oracle 9i, by which we can fetch queries or database statements that are running slow in the entire database on a weekly basis ?

Wow, it's still in use...

I think you need something like [http://www.optier.com/](http://www.optier.com/).

But before you go this route, I suggest you identify what it means to be slow look at "explain plan" for each of those queries, etc...

Only then you should start looking at tools like OpTier...

---

