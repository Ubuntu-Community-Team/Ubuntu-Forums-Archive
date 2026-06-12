---
title: "Sql count()"
date: 2011-03-06
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-03-06
Hello there,

i am working on a database for a survey i am making at the moment.

I have a column "Block" which can have a value of 1 to 21. If i want to count how many entries have the value "1" in "Block" then i use COUNT() no problem.
What i'd like to achieve however is to count how many entries there are for each possible value in "Block". In other words how many entries have Block=1, how many Block=2 etc... till Block=21.
I played around thinking JOIN would help, but SQL gets confused as well as with ALIAS.
For instance it goes fine as far as this is queried ...
[PHP]SELECT "Block" AS "Block1", "Block" AS "Block2" FROM "interviews" WHERE "Block1"=1 OR "Block2"=2[/PHP]
... but gets messy when querying:
[PHP]SELECT COUNT("Block") AS "Block1", COUNT("Block") AS "Block2" FROM "interviews" WHERE "Block1"=1 OR "Block2"=2[/PHP]

Any idea how to do that?

Thanks.
Benjamin

---

### Post by v8YKxgHe on 2011-03-06
```
SELECT foo, COUNT(foo) FROM bar GROUP BY foo
```

---

