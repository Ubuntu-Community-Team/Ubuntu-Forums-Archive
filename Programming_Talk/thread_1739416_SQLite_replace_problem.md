---
title: "SQLite replace problem"
date: 2011-04-25
forum: Programming Talk
---

### Post by papibe on 2011-04-25
I'm trying to do the following replace with no luck (using SQLite from the repositories):
```
UPDATE path
SET strPath = REPLACE(strPath,'smb://REINHARDT/Media Library/Movies/','/nfs/ml1/Movies/')
WHERE strPath LIKE 'smb://REINHARDT/Media Library/Movies/%';
```
I made work in 2 steps, using a dumb-pattern, like this:
```

UPDATE path
SET strPath = REPLACE(strPath,'smb://REINHARDT/Media Library/Movies/','dumb-pattern')
WHERE strPath LIKE 'smb://REINHARDT/Media Library/Movies/%';

UPDATE path
SET strPath = REPLACE(strPath,'dumb-pattern','/nfs/ml1/Movies/')
WHERE strPath LIKE 'dumb-pattern%';

```
But I still don't understand why the first code doesn't work.

I appreciate any hits or ideas.
Regards.

---

### Post by papibe on 2011-04-26
b.u.m.p.

---

### Post by papibe on 2011-04-29
Any idea?

---

### Post by carchaias on 2011-10-17
I had exactly the same experience. I can't replace one path against another. What i found was that if using one more or one less / in one of the argument paths at beginning or end of the string  the sql thing works like crazy. Unfortunately there is one / to much or to less in the path then... I spent some houres to day to find a solution but it seams there is nothing in the net ....? And you even cant replace '/' vs ". 
I tried with sqliteman :(

---

### Post by carchaias on 2011-10-21
Now i suppose it is due to the unique flag in the colum to change . Replace would have to produce dublicates in the colum and that's why the process stops. Sorry mz problem was on the sqlitdb  from shotwell...

---

