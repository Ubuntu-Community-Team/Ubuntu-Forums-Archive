---
title: "How to increment a column in AWK"
date: 2011-06-29
forum: Programming Talk
---

### Post by hailholyghost on 2011-06-29
Hi,

I want to make a graph of the Karplus function 

f($1) = 15.3*(cos((180/$pi)*$1+120))**2-6.2*cos((180/$pi)*$1+120)+1.5

I want to make the text file with AWK, as a learning experience to get away from Libre Office.

I want it to look like

0  f(0)
1  f(1)
2  f(2)
3  f(3)

etc. so I can graph it easily with Grace.  I've found numerous reference to this working *from* another file but never *creating* one from awk.

I thought of something like (pca is a perl math script, and this doesn't work)
```

awk 'BEGIN {t=0} {print $1, pca '15.3*(cos((180/3.14)*$1+120))**2-6.2*cos((180/3.14)*$1+120)+1.5', t++}'
```

but I can't find information about how far to take the incrementation.

Your help is greatly appreciated!
-Dave:D

---

### Post by geirha on 2011-06-29
Use a for-loop in the BEGIN block.
```
awk '
BEGIN {
  for (t=0;t<100;t++) {
    print t, 15.3*...;
  }
}'

```

What you're doing now is doing the calculation of the first field of each line of input, but it doesn't sound like you want that.

---

### Post by hailholyghost on 2011-06-30
Thank you very much geirha!  It worked beautifully!

---

