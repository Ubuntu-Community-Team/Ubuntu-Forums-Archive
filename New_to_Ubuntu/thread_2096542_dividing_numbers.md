---
title: "dividing numbers"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by jhuuht9 on 2012-12-20
I defined in my ssh linux server

a="(less Msignalcrs)"

b=$(less Msqrt)

echo $"(($a / $b))" |bc
3

I would like to get my output in decimals when I'm trying to divide a over b, but cannot. How is my program wrong?

---

### Post by drmrgd on 2012-12-20
The problem is the the dual parenthesis along with not setting the precision that you want.  Try something like this (for 2 decimal places let's say):

```

echo "scale=2; $a/$b" | bc

```

---

