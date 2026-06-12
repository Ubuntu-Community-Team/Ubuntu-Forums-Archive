---
title: "[SOLVED] generating a random number in python"
date: 2008-03-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-03-11
I want to give a random number,
that is smaller than 10 to a variable.

Thanks.

---

### Post by WW on 2008-03-11
Take a look at the **random** module.  Try this:
> 
>>> import random
>>> help(random)

or look [here](http://docs.python.org/lib/module-random.html).

Do you want integers or floating point numbers?

---

### Post by crazyfuturamanoob on 2008-03-11
Integers. 
But im curious and 
want to know how to 
get floating point numbers too.

---

### Post by Wybiral on 2008-03-11
The "random" module has all kinds of generators (integer and float as well as different distributions).

---

### Post by WW on 2008-03-11
For integers, use **randrange**:
> 
>>> import random
>>> random.randrange(10)
8
>>> random.randrange(10)
0
>>> random.randrange(10)
1
>>>

For floating point numbers, the basic function is **random**, which creates numbers in [0,1):
> 
>>> random.random()                              
0.90300988531330029
>>> random.random()
0.50559672165513858
>>> random.random()
0.73444115443236646
>>> 


---

### Post by crazyfuturamanoob on 2008-03-11
> 

For integers, use randrange:
[QUOTE]>>> import random
>>> random.randrange(10)
8
>>> random.randrange(10)
0
>>> random.randrange(10)
1
>>>

[/QUOTE]
Thank, but you forgot to put the rest 2
arguments to randrange (start,end,step).

---

### Post by WW on 2008-03-11
Those arguments are optional.  Fire up python and try it out:
> 
>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> random.randrange(10)
9
>>> random.randrange(10)
5
>>> random.randrange(10)
5
>>> range(100,125,5)
[100, 105, 110, 115, 120]
>>> random.randrange(100,125,5)
105
>>> random.randrange(100,125,5)
120
>>> random.randrange(100,125,5)
110
>>> random.randrange(100,125,5)
105
>>> 


---

