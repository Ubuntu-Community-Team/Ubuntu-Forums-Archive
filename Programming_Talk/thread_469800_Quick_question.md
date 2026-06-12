---
title: "Quick question"
date: 2007-06-10
forum: Programming Talk
---

### Post by DeadPanDan on 2007-06-10
Could someone please explain to a noob what is going on here?
> 
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 5.2 - 5.0
0.20000000000000018
>>> 
5.2 - 5.0 = 0.20000000000000018???

---

### Post by nitro_n2o on 2007-06-10
well... nothing, everything seems to be fine :) 
The way floats are represented on a machine isn't what do you expect always, thus you never compare two floats for equality!.. Some Alan Turing writings do talk about this..
But for now you can read this: 
[http://www.cprogramming.com/tutorial/floating_point/understanding_floating_point.html](http://www.cprogramming.com/tutorial/floating_point/understanding_floating_point.html)

---

### Post by DeadPanDan on 2007-06-10
Thanks. That'll keep me busy. :)

---

### Post by pmasiar on 2007-06-10
float number use binary approximation of decimal value.

You did know that number pi is not 3.14, and not even 3.1415926, right? All this is approximation, nad you need to round results and not use them as provided - least significant digits are *always* wrong by design.

You can also use "long" integers, which are always exact (no rounding) how that arithmetics is obviously slower.

---

