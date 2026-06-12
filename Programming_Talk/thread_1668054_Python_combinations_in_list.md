---
title: "Python combinations in list"
date: 2011-01-15
forum: Programming Talk
---

### Post by n~kf)}BW% on 2011-01-15
I would like to create a function that works as followed:

```
list = ['apple','banana','lemon','orange']

def combos(list, number):
 ...

```
combos(list,2)
['apple','banana'],['apple','lemon'],['apple','orange'],['banana','orange'],['banana','lemon'],['lemon','orange']

combos(list,1)
['apple'],['banana'],['lemon'],['orange']

Please help me figure it out :) Thanks!

PS: What is this even called? It's not Cartesian product...

---

### Post by schauerlich on 2011-01-15
[itertools.combinations()](http://docs.python.org/library/itertools.html#itertools.combinations)

---

### Post by CptPicard on 2011-01-16
[http://ubuntuforums.org/showthread.php?t=649295&highlight=combinations](http://ubuntuforums.org/showthread.php?t=649295&highlight=combinations)

---

### Post by unknownPoster on 2011-01-16
Seriously, the first link in the Google search for "Python List Combinations" gives you exactly what you want. If you want to get help here, you need to put in some work yourself.

---

### Post by wmcbrine on 2011-01-16
> **slovenia said:**
> PS: What is this even called? It's not Cartesian product...[Combinatorics.](http://www.youtube.com/watch?v=w0i_ZFlGTVY)

---

### Post by n~kf)}BW% on 2011-01-16
> **unknownPoster said:**
> Seriously, the first link in the Google search for "Python List Combinations" gives you exactly what you want. If you want to get help here, you need to put in some work yourself.

Hey man, you got me wrong... I want to do this myself. I don't like to include itertools for just one call in my whole program...

Thanks for the help people, anyway...

---

### Post by ziekfiguur on 2011-01-16
> **slovenia said:**
> I don't like to include itertools for just one call in my whole program...

Why not use
```
from itertools import combinations
```

---

### Post by ziekfiguur on 2011-01-16
sorry

---

### Post by wmcbrine on 2011-01-17
> **slovenia said:**
> I don't like to include itertools for just one call in my whole program...If it's just one call, it makes *more* sense to import it, rather than devoting a bunch of code to it. Importing it isn't that much overhead. The only reason I might avoid it would be to maintain compatibility with Python < 2.6.

Anyway, check out the implementation linked in #2 -- that's what you'd have to do instead.

---

### Post by n~kf)}BW% on 2011-02-02
Thank you :) You have both been helpful. I'll import combinations from itertools. Didn't know you could do it that way

---

