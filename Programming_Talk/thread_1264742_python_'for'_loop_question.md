---
title: "python 'for' loop question"
date: 2009-09-12
forum: Programming Talk
---

### Post by donkyhotay on 2009-09-12
This is a basic question about programming in python. I'm trying to create a for loop that takes a random variable and increments by a specific amount each time it's run (in the example the number is 10). I just want to make certain that
```

for x in range(variable, (variable + 10)):

```
is correct. So that basically if the variable happens to be 5, x will increment from 5-15 and if variable happens to be 10, x will increment from 10-20. I don't usually use for loops in python and C++ handles this issue very differently so I would like to doublecheck this statement with someone before I potentially mess up the code in my project.

---

### Post by Yannick Le Saint kyncani on 2009-09-12
Just fire up the python interpreter :

```

/home/kyncani/ > python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:58:18)
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print range.__doc__
range([start,] stop[, step]) -> list of integers

Return a list containing an arithmetic progression of integers.
range(i, j) returns [i, i+1, i+2, ..., j-1]; start (!) defaults to 0.
When step is given, it specifies the increment (or decrement).
For example, range(4) returns [0, 1, 2, 3].  The end point is omitted!
These are exactly the valid indices for a list of 4 elements.
>>>
/home/kyncani/ >

```

---

### Post by Can+~ on 2009-09-12
> **donkyhotay said:**
> This is a basic question about programming in python. I'm trying to create a for loop that takes a random variable and increments by a specific amount each time it's run (in the example the number is 10). I just want to make certain that
```

for x in range(variable, (variable + 10)):

```
is correct. So that basically if the variable happens to be 5, x will increment from 5-15 and if variable happens to be 10, x will increment from 10-20. I don't usually use for loops in python and C++ handles this issue very differently so I would like to doublecheck this statement with someone before I potentially mess up the code in my project.

I'm not sure if this is what you want, do you want to jump from X to X+10, X+20, X+30? Or just iterate from X to X+10?

If you have doubts, the python for .. in .. iterator works like this:

```
for return_value in object.next()
```

Every object that's iterable, has an next() method, and for just calls it until it raises an internal signal. In the case of iterating through numbers:

```
for i in xrange(start, stop, step)
```

It's identical to C's (and C++'s) for, in the sense of:

```
for (i=start; i < stop; i += step)
```

And python's 2.6 range():

```
for i in range(start, stop, step)
```

Works like having just a list of data:

```
for i in [start, start+step, start+step*2, ... , end-step, end] 
```

I hope that made it clearer.

---

### Post by wmcbrine on 2009-09-12
> **donkyhotay said:**
> C++ handles this issue very differentlyThere's an understatement. :) In Python, "for" iterates over a list, or other iterable. So basically, all the values are worked out beforehand, before the first iteration. (There are exceptions, but let's not go into that now.) To do a C-style loop, where the value of the loop variable is updated after each iteration, in Python you'd have to use "while".

In your example, the step parameter of range() will do what you need. But notice that range() *is not part of the "for" loop*; it just returns a list that "for" then iterates over. So you could do this:

```

loop = range(5, 26, 10) # loop == [5, 15, 25]
for i in loop:
    print i

```

just as well as "for i in range" etc. Alternatively:

```

loop = 5
while loop < 26:
    print loop
    loop += 10

```

---

### Post by donkyhotay on 2009-09-12
Thanks for the clarification, your probably right in my wanting a 'while' loop rather then a 'for' loop. Although my C++ is really rusty these days, I use 'for' loops in python so rarely then when I need one I get them mixed up with C++ and try to use them the same way.

---

### Post by wmcbrine on 2009-09-12
Python's "for" is extremely useful, though. Where in C, you might do something like:

```

for (i = 0; i++; i < 10)
    printf("%d\n", somevar[i]);

```

in Python, it could be:

```

for x in somevar:
    print x

```

Basically, you can do away with explicit indexing in many situations.

---

### Post by Copernicus1234 on 2009-09-13
While is also much slower than for in python.

---

### Post by nvteighen on 2009-09-13
Yes, but sometimes you need while in order to control the loop's progression in a non-iterator fashion...

One has to use what works... :p

---

