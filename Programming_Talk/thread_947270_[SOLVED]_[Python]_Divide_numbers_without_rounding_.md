---
title: "[SOLVED] [Python] Divide numbers without rounding them automatically?"
date: 2008-10-14
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-14
Python automatically rounds answers with dividing.


If I use the calculator program that comes with ubuntu:
92 / 255 = 0,360784314

But when I do it with python interactive console, I get:
92 / 255 = 0


So how to prevent that auto-rounding? :confused:

---

### Post by Greyed on 2008-10-14
Don't divide using integers.

```

>>> 92.0 / 255.0
0.36078431372549019

```

Or, more completely, learn about Python's different data types.

---

### Post by CptPicard on 2008-10-14
+1... it is not "auto-rounding", it is perfectly correct integer division...

---

### Post by WW on 2008-10-14
Eventually the Python language will change so that division of integers automatically converts the arguments to floating point.  You can access this behavior now by putting the statement
```

from __future__ import division

```
in your code.  Then division of integers will behave the way you want.

For example,
```

>>> 10/3
3
>>> from __future__ import division
>>> 10/3
3.3333333333333335
>>> 10/2
5.0
>>> 92/255
0.36078431372549019
>>> 

```

---

### Post by Greyed on 2008-10-14
Ierrrr, what got into Guido's head for that to go through?

---

### Post by NovaAesa on 2008-10-14
> **WW said:**
> ... Then division of integers will behave the way you want.

To me that seems somewhat... ridiculous. Every other programming language I know does integer division when presented with integers and floating point division when presented with floating point numbers. It doesn't seem like a good idea IMO to make things inconsistent just to appease beginners who might not understand the typing system correctly.

---

### Post by CptPicard on 2008-10-14
My suspicion about the rationale is that it's got to do with "least surprise" with duck typing. If you have two variables, a and b which you know are at least numeric values, then a / b always produces a floating-point division result regardless of whether one or both are int. The point being here that you might actually get a nasty surprise if you're manipulating a bunch of number variables, and then all of a sudden, under the hood, two of them happen to be integers, and you get an integer division result.

I have to agree that it sounds odd from a programmer's perspective and I don't like it, but... that could be a reason.

---

### Post by Greyed on 2008-10-14
But... but... that is what a / float(b) is for.

Le sigh....  I dropped Perl because of stuff like this.  :/

---

### Post by babyhuey on 2008-10-14
I don't really see the problem here. I would think the majority of the time people want to use floating point division. Seems logical that the default ' / ' operator would perform floating point and ' // ' uses the exception, integer division. 

Whether or not it *needs* changing is a different story. I must say I'm glad python is being progressive. There are plenty of languages that stick with tradition. -I feel like I'm coming off as a liberal =)

---

### Post by dribeas on 2008-10-15
> **NovaAesa said:**
> To me that seems somewhat... ridiculous. Every other programming language I know does integer division when presented with integers and floating point division when presented with floating point numbers. It doesn't seem like a good idea IMO to make things inconsistent just to appease beginners who might not understand the typing system correctly.

I would assume that it goes just in the same line as integers promoting to bigger size integer types once they would overflow. You can always back convert to an integer type to loose those 'unwanted' decimals.

---

