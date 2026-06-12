---
title: "Python large numbers"
date: 2010-09-25
forum: Programming Talk
---

### Post by kroq-gar78 on 2010-09-25
Hello Ubuntu Forums community,

I am making a python program that requires the math.pow function. I need it to go up to 2^31 (2 to the 31st power) and preferably even farther. When I run the program in the terminal, it says "OverflowError: math range error"

Any way to fix this?
Thanks in advance.

---

### Post by Bachstelze on 2010-09-25
What are you doing, exactly? math.pow(2, 32) doesn't raise an exception for me.

---

### Post by Queue29 on 2010-09-25
Python supports arbitrary precision numbers out of the box. What version are you using? And can you post the code that seems to be troublesome?

---

### Post by ssam on 2010-09-25
> **Queue29 said:**
> Python supports arbitrary precision numbers out of the box. What version are you using? And can you post the code that seems to be troublesome?

thats not right. its just long ints that have infinite range.

[http://docs.python.org/library/stdtypes.html#numeric-types-int-float-long-complex](http://docs.python.org/library/stdtypes.html#numeric-types-int-float-long-complex)

```
>>> math.sin(pow(2,1000))
-0.15920170308624243
>>> math.sin(pow(2,10000))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OverflowError: long int too large to convert to float
```

---

### Post by worksofcraft on 2010-09-25
> **ssam said:**
> thats not right. its just long ints that have infinite range.

[http://docs.python.org/library/stdtypes.html#numeric-types-int-float-long-complex](http://docs.python.org/library/stdtypes.html#numeric-types-int-float-long-complex)

```
>>> math.sin(pow(2,1000))
-0.15920170308624243
>>> math.sin(pow(2,10000))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OverflowError: long int too large to convert to float
```

I thought it would calculate pow as floating point number anyway... what on Earth is Python doing... 10000 multiplications?

Anyway as far as I can tell most languages use floating point as provided by their processor which is usually IEEE-754. I think it  give about 16 digits of precision and exponent up to something like 300 in decimal.

---

### Post by Bachstelze on 2010-09-25
> **worksofcraft said:**
> I thought it would calculate pow as floating point number anyway... what on Earth is Python doing... 10000 multiplications?

pow is integer, math.pow is float.

```
>>> pow(2, 1000)
10715086071862673209484250490600018105614048117055336074437503883703510511249361224931983788156958581275946729175531468251871452856923140435984577574698574803934567774824230985421074605062371141877954182153046474983581941267398767559165543946077062914571196477686542167660429831652624386837205668069376L
>>> math.pow(2, 1000)
1.0715086071862673e+301

```

Incredible as it may sound, having integer powers is actually very useful. When doing arithmetic for example.

---

### Post by kroq-gar78 on 2010-09-25
Thanks Bachstelze. I didn't know there was just pow() and that there was a difference between pow() and math.pow().

Marking thread as solved.

---

### Post by Bachstelze on 2010-09-26
> **kroq-gar78 said:**
> Thanks Bachstelze. I didn't know there was just pow() and that there was a difference between pow() and math.pow().

Marking thread as solved.

Yup, this is why you should never do

```
from math import *
```

---

### Post by CptPicard on 2010-09-26
> **Bachstelze said:**
> pow is integer, math.pow is float.


Well, unless you give pow float parameters.

That math.pow is specifically a float is interesting; could be one of these rare cases where I might actually agree with worksofcraft's objections to Python's handling of number types.

---

### Post by Bachstelze on 2010-09-26
> **CptPicard said:**
> Well, unless you give pow float parameters.

That math.pow is specifically a float is interesting; could be one of these rare cases where I might actually agree with worksofcraft's objections to Python's handling of number types.

It makes sense to me.  As I said, in some applications you really want full-precision exponentiation of integers (e.g. when doing RSA crypto), but on the other hand, sometimes you don't need the precision, and having long integers is just a bother.

Having both is a nice thing about Python IMO.

---

### Post by CptPicard on 2010-09-26
> **Bachstelze said:**
> 
Having both is a nice thing about Python IMO.

Yeah, but it should then be pythonically generic, output according to input, as in pow, and not inconsistent in math.pow with that idea with a requirement to just know that this is how math.pow works. That's my only objection to it really.

---

### Post by Bachstelze on 2010-09-26
I don't know, it's intuitive enough to me: math.pow always returns float, and pow returns int when it makes sense (like addition, you can't really expect it to return int when you give it float arguments). I must admit I never use pow, though, I use ** for integer exponentiation, and math.pow for floats.

---

### Post by Wybiral on 2010-09-26
> **CptPicard said:**
> Yeah, but it should then be pythonically generic, output according to input, as in pow, and not inconsistent in math.pow with that idea with a requirement to just know that this is how math.pow works. That's my only objection to it really.

I agree. It's "import math" not "import floatmath" (which is more like what it really is). Though, I still feel like integer overflow should result in bignum :) But, I also feel like floating point overflow should result in decimal/rational representation... Not range exceptions.


> **Bachstelze said:**
> I must admit I never use pow, though, I use ** for integer exponentiation, and math.pow for floats.

I use "pow" all the time. It works as you'd expect it to work, pow(2.0, 2) == 4.0, pow(2, 2) == 4. The math module to me is just for trig functions and floor/ceil.

---

### Post by jpkotta on 2010-09-26
From [http://docs.python.org/library/math.html:](http://docs.python.org/library/math.html:)
> This module is always available. It provides access to the mathematical functions defined by the C standard.

It makes sense then, because the C math library functions return double (ignoring the variants that take floats and longs).  math.pow() works like C's pow() instead of Python's pow().

---

### Post by nvteighen on 2010-09-27
> **jpkotta said:**
> 
It makes sense then, because the C math library functions return double (ignoring the variants that take floats and longs).  math.pow() works like C's pow() instead of Python's pow().

No, it doesn't make sense: it adds a weird inconsistency in the language. While the rest works generically, lots of times hiding the details of the C Standard Library, math.pow doesn't and brings in requirements that are out of place in a duck-typed language. Ok, you may say it's a minor issue because there's pow(), but it confused the OP, who is a beginner... how many other beginners may have fallen into this pitfall?

---

### Post by Bachstelze on 2010-09-27
> **nvteighen said:**
> No, it doesn't make sense: it adds a weird inconsistency in the language.

What's the inconsistency?  All the functions in math return a float, seems pretty consistent to me.  The confusing thing is that there's pow and math.pow, which are different, but that's a questionable design choice, not an inconsistency.

---

### Post by nvteighen on 2010-09-27
> **Bachstelze said:**
> What's the inconsistency?  All the functions in math return a float, seems pretty consistent to me.  The confusing thing is that there's pow and math.pow, which are different, but that's a questionable design choice, not an inconsistency.

The inconsistency lies in that where everything in Python is meant to work as generically as possible, there you have math.pow as a float-specific power function and pow as a generic power function, when only one should actually exist (the second). If someone needs to make a float of an int, then he should cast it, not the language.

---

### Post by jpkotta on 2010-09-27
> **Bachstelze said:**
> What's the inconsistency?  All the functions in math return a float, seems pretty consistent to me.  The confusing thing is that there's pow and math.pow, which are different, but that's a questionable design choice, not an inconsistency.

> **nvteighen said:**
> The inconsistency lies in that where everything in Python is meant to work as generically as possible, there you have math.pow as a float-specific power function and pow as a generic power function, when only one should actually exist (the second). If someone needs to make a float of an int, then he should cast it, not the language.

To me, math.pow is not part of Python, but pow is.  math.pow is a library function that happens to come with Python, and thus doesn't have all of the expectations of pow.  But it definitely seems silly to have two functions that do the same thing, especially when one does it poorly.

BTW, pow is really a method call, like len and repr.

---

