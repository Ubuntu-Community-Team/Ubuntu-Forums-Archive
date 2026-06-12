---
title: "Python 'zip' question"
date: 2006-11-14
forum: Programming Talk
---

### Post by kinghajj on 2006-11-14
I know that Python's zip() function will take, say, (1,2) and (3,4) and return [(1,3), (2,4)]. I, however, need a function that will take [(1,2), (3,4)] and return the same. I don't know how long the list might be, though; for all I know it could be [(1,2,3,4), (5,6,7,8), (9,10,11,12)], so splitting the list in two won't work (as there might be many more than two sequences in the list).

All help is greatly appreciated. Thanks.

Edit:

I found the answer. If you write "zip(*table)" and table is, for example, [ (1,2), (3,4)], the function returns what I wanted.

---

