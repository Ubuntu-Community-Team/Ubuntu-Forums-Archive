---
title: "Maths question about notation"
date: 2012-10-23
forum: Programming Talk
---

### Post by xytron on 2012-10-23
Please look at the image below.

What does the following notation mean?

```
 a.AA'+b.BB'=0 

```



specifically what is;

a.AA'

what does the period mean here?

thanks
[IMG]http://www.hyperscope.net/mob.png[/IMG]

---

### Post by muteXe on 2012-10-23
the vector dot product?
[http://en.wikipedia.org/wiki/Dot_product](http://en.wikipedia.org/wiki/Dot_product)
what's this got to do with programming?

---

### Post by Vaphell on 2012-10-23
> what's this got to do with programming?

nothing but where would you go to find people with high levels of math expertise without signing in to some math forum? Programming forum would be the next best bet.

---

### Post by muteXe on 2012-10-23
Like you said, a maths forum.

---

### Post by spjackson on 2012-10-23
I am reasonably sure that the dot here is simply scalar multiplication.

(The unsigned length of the red line segment a multiplied by the signed length AA') plus (the unsigned length of the blue line segment b multiplied by the signed length BB') is 0.

Hence:
```

a/b = - BB'/AA'

```
Setting aside the issue of signed lengths, we know these ratios are equal because PAA' and PBB' are congruent triangles.

---

