---
title: "python : testing condition on numbers"
date: 2010-09-21
forum: Programming Talk
---

### Post by wlourf on 2010-09-21
Hello python's gurus !

With this simple code :
```
x=19.9
while x<20.1:
    x+=0.01
    print x, x==20,x==20.0

```i except to have an output like this :
```
...
19.95 False False
19.96 False False
19.97 False False
19.98 False False
19.99 False False
[COLOR=Red]**20.0 True True**[/COLOR]
20.01 False False
20.02 False False
20.03 False False
...

```but values are always set to False.

I know I miss something but don't know what ! I try to use float long bur without success.

NB :  With  str(x)=="20.0", that's ok but I'm looking for a more "clean" solution.

Thanks for any help !

---

### Post by Bachstelze on 2010-09-21
Rounding errors. ;)

```
>>> x = 19.9
>>> while x < 20:
...     x += 0.01
...     print x, x == 20, x == 20.0
... 
19.91 False False
19.92 False False
19.93 False False
19.94 False False
19.95 False False
19.96 False False
19.97 False False
19.98 False False
19.99 False False
20.0 False False
>>> x
20.000000000000014

```

Clean solution: work with integers.

---

### Post by wlourf on 2010-09-21
arrrrh ok 
on my computer, output is 
```
20.10000000000003
```To work with integers, is this the correct way ?
```
x=1990
while x<2010:
    x+=1
    print x/100.0, x/100.0==20.0   
```
what do you think ?

---

### Post by Bachstelze on 2010-09-21
This is fine. 2000/100.0 does exactly equal 20. You don't really need to divide, though, just test for [font=monospace]x == 20*100[/font].

---

### Post by wlourf on 2010-09-21
thanks ! et bonjour à Bordeaux !

---

### Post by StephenF on 2010-09-21
Comparing binary floating point numbers for equality based on presumptions derived from base 10 arithmetic is not a good idea. It's one of the traps new programmers fall into.

Fortunately Python has a module for floating point arithmetic in base 10 that will take those neat often rounded for human consumption numbers and play nice with them.
[http://docs.python.org/library/decimal.html](http://docs.python.org/library/decimal.html)

---

