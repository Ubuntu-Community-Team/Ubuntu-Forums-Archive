---
title: "easy SQL question"
date: 2006-02-28
forum: Programming Talk
---

### Post by jerome bettis on 2006-02-28
i'm still learning SQL and i can't find if there's a better way to do this.  i have two tables

```
Batting
playerID    G    H   AB ....
"abcde01"  10    3    32

Master
playerID .... nameFirst  nameLast
"abcde01" ..  "abc"       "defgh"
``` 
what i want to do is select stuff from the batting table, but i need to get the player's first and last names from the master table, using the playerID i got from the first table.  right now i'm just using 2 select stmts, but i think there should be a better way to do this??

in other words instead of printing
abcde01  10  3 32

i want to say
defgh, abc 10 3 32

without having to do 2 selects

thx

---

### Post by thumper on 2006-02-28
```
select m.nameFirst, m.nameLast, b.g, b.h, b.ab
from Master m, Batting b
where m.playerID = b.playerID
```

---

### Post by thumper on 2006-02-28
Oh, and you can easily add extra bits to the where clause to further reduce your result set.

---

### Post by jerome bettis on 2006-02-28
thanks that's perfect!

---

### Post by sapo on 2006-02-28
You can also use a simple JOIN:

```
select m.nameFirst, m.nameLast, b.g, b.h, b.ab
from Master m
JOIN Batting b ON (m.playerID = b.playerID)
```

This is simple, but you can take some time a read a little about join, for writing big queries using "where" makes it kinda hard to read, but thats not the case on yours ;)

---

