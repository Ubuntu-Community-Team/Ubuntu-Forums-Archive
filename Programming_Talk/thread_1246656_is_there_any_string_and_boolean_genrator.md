---
title: "is there any string and boolean genrator??"
date: 2009-08-22
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-22
just by curiosity, how to generate random strings? all i know is int,float and double can be genrated, if there would be a boolean and string genrators, let me know how to do it, maybe in c++ or java........

---

### Post by lisati on 2009-08-22
I have an idea: for letters, generate a random number from 0 to 25, then add the ASCII code for 'A', and repeat for however many letters you need in your string.

---

### Post by Can+~ on 2009-08-22
Characters are just numbers, if you know how to create random numbers, then you can do it with strings.

[PHP]#!/usr/bin/env python

from random import randint

gen = lambda l: "".join(chr(randint(ord('a'), ord('z'))) for i in xrange(l))

print gen(20)[/PHP]

And a boolean generator? Flip a coin?

---

### Post by abhilashm86 on 2009-08-22
> **Can+~ said:**
> Characters are just numbers, if you know how to create random numbers, then you can do it with strings.


And a boolean generator? Flip a coin?

oh thats cool!!
```
bool status=flip(coin)?true:false;
```:guitar::

---

### Post by Tony Flury on 2009-08-22
The simplest Boolean generator would be to generate a random number, and test if the number is odd.

Make sure that the length of the range is even (so you know you have a 50/50 chance of getting an even/odd number - 0 to 9 would be ok for instance.

---

