---
title: "python roots problem"
date: 2007-02-07
forum: Programming Talk
---

### Post by oldmanstan on 2007-02-07
when i do this:

```
64**(1.0/3.0)
```

python gives me

```
3.9999999999999996
```

is this just a quirk of my particular machine or is this python?  i mean, is there a way around this inaccuracy or will i just have to live with it?  obviously i can understand why this happens, but i need it to be more accurate, any solutions?

thanks

---

### Post by neilp85 on 2007-02-07
I get the same thing. There are several python packages out there for scientific computing which provide more accuracey.

---

### Post by ssam on 2007-02-07
thats 1 part in 10^15, which is pretty accurate. if you need more accuracy then there should be a library to help you do this. there is  GNU Multiple Precision Arithmetic Library for C, and there seems to be a python wrapper for it.

if you are more worried about printing the number to screen and it looking nice, then you just need to round it. the print command will round it automatically.

in the python interpreter:
```

>>> 64**(1.0/3.0)
3.9999999999999996
>>> print 64**(1.0/3.0)
4.0

```

---

### Post by pmasiar on 2007-02-07
> **oldmanstan said:**
> when i do this:

```
64**(1.0/3.0)
```

python gives me

```
3.9999999999999996
```

is this just a quirk of my particular machine or is this python?  i mean, is there a way around this inaccuracy or will i just have to live with it?  obviously i can understand why this happens, but i need it to be more accurate, any solutions?

thanks

What do you mean "more accurate"? You expected result be integer 4? Floating point arithmetics is not "that" accurate - good beginner exercise is to write a program to calculate epsilon - the smallest floating nuber which: 1.0 + epsilon = 1.0. :-)

Integer numbers do not make sense in real world - real world measures are not integers. If you measure something as 64 inches (or cm, or lightyears) long, it might be 63.99999999999997 or 64.0000000000002 and it is the same thing. Real world does not wave nice numbers as math theory does. Ie. do you know that moon is slowing rotation of the Earth and astronomers occasionally need to add "lapse second" so astronomic time does not stray away?

What kind of problems you are trying to solve that you need more accuracy?

---

### Post by oldmanstan on 2007-02-07
maybe accuracy was the wrong word to use since really i'm not looking for "accuracy" per se.  what i'm doing is writing a function to find perfect cubes.  and since
```
3.9999999999999996 % 1 != 0
```
it's messing me up.  i'm teaching myself python and this is just part of a little number excercise i'm doing.

is there another way to calculate roots then that is exact?  i mean, i guess i could just try to guess them them and test numbers until i hit one that's too high but that would be way more expensive computationally (i would imagine).  i had thought about trying to round out to a certain number of decimal places but then the number that i rounded to would basically be arbitrary and in theory i think i might run into a number that it would think was a cube but actually wasn't... i dunno.  another idea i had would be to just round the root then raise it to the 3rd power, if i get back the exact original number then it was a true root (since if i get back 2.0 say the rounding wouldn't change it).  but this would, again, probably be expensive it seems to me...  any thoughts anyone?

thanks!

---

### Post by ssam on 2007-02-07
you might have to change your test to whether the result is close to 0 (or 1).

you will find numbers which pass this test falsely, but think you will be having other precision problems by then, eg

```

>>> 10000000000000000.0 + 1
10000000000000000.0

```

---

### Post by jblebrun on 2007-02-07
> **oldmanstan said:**
> maybe accuracy was the wrong word to use since really i'm not looking for "accuracy" per se.  what i'm doing is writing a function to find perfect cubes.  and since
```
3.9999999999999996 % 1 != 0
```
it's messing me up.  i'm teaching myself python and this is just part of a little number excercise i'm doing.

thanks!


Which algorithm are you using to find the roots?

---

### Post by oldmanstan on 2007-02-07
> **jblebrun said:**
> Which algorithm are you using to find the roots?

at the moment i'm just doing the roots like this
```
import math

def is_root(number, root):
	if math.exp(1/root*math.log(number)) % 1 == 0:
		return 1
	else:
		return 0
```
but i also tried the simpler looking
```
def is_root(number, root):
	if number**(1.0/root) % 1 == 0:
		return 1
	else:
		return 0
```

is that what you meant?

thanks

---

### Post by jblebrun on 2007-02-07
Ok, I see. Well, as someone has already mentioned, if you're using floating point variables, there's always going to be some issues with accuracy. When you calculate functions like exponents or logs, iterative numerical methods are used. These can get very very close to the right answer, but may not always hit it exactly. This is combined with the issue that some numbers simply can not be fully represented in floating point. 

So, your best bet is to define a tolerance... how accurate you want to be. Then just change  the "==0" to  "< tolerance". 

In what sort of context are you using your is_root function? Is it helping you make decisions in some sort of iterative numerical algorithm?

---

### Post by pmasiar on 2007-02-07
> **oldmanstan said:**
> is there another way to calculate roots then that is exact?

you may convert results of your calculations to integer, find the difference, and if close enough - replace results with new integer. 

Be carefull tho: dividing integers is not the same as dividing floats: result of dividing integers is rounded to integer! 

>>> x = 3
>>> x/5
0
>>> x = 3.0
>>> x/5
0.59999999999999998

This is now considered bad design by Guido and IIRC will go away in Python3K

---

### Post by oldmanstan on 2007-02-07
> **jblebrun said:**
> In what sort of context are you using your is_root function? Is it helping you make decisions in some sort of iterative numerical algorithm?

it's really very simple, i'm using it to find numbers a, b and c such that a^n + b^n = c^n in a given range where n > 2

it does absolutely nothing useful, just a learning tool since number problems are fun to code and lend themselves to computation

i could have done it "quick and dirty" (see my post above, i list a couple ways i thought of) but the other ways i came up with weren't very efficient in terms of speed, i figured i would try to make it as fast as possible as part of the learning process.

---

### Post by lloyd mcclendon on 2007-02-07
since floating point math will never be right, you have to have a margin for error

```
#!/usr/bin/env python

import math

epsilon = 0.000000001 # adjust as you see fit

def isRoot(number, root):
    root = math.pow(number, 1.0 / root)
    rounded = round(root)
    return (root < rounded and rounded - epsilon < root) or \
                  (root > rounded and rounded + epsilon > root)

if __name__ == "__main__" :
    for i in range(1, 1000)  :
        if (isRoot(i, 3))  :
            print str(i) + " is a cube root!"
```

---

### Post by lloyd mcclendon on 2007-02-07
actually the return value could be better expressed as

    return math.fabs(rounded - root) < epsilon

---

### Post by dwblas on 2007-02-08
decimal.Decimal() is supposed to take care of that although I haven't used it.  If you come up with any good code snippets, please post them as we all might want to use this at some time.
[http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html)
[http://pydoc.org/2.4.1/decimal.html#Context-power](http://pydoc.org/2.4.1/decimal.html#Context-power)

---

### Post by QwertyManiac on 2008-03-04
Thank you for your decimal module suggestion, using it seems to work just fine!

Here's my comparing snippet from the interpreter mode:

*Knowing that **41063625** is the cube of 345*

```
>>> from decimal import *
>>> 41063625**(1/3.0)
344.99999999999989
>>> **Decimal(str(41063625**(1/3.0)))**
Decimal("345.0")
>>> Decimal(str(41063625**(1/3.0))) == 345
True
>>> 41063625**(1/3.0) == 345
False
```

And of course, changing a value even by a unit makes no impact on its accuracy:
```
>>> Decimal(str(4106362**6****(1/3.0))) == 345
False
>>> Decimal(str(4106362**4****(1/3.0))) == 345
False
```

---

