---
title: "How to get number of non-empty entries in arrays in C"
date: 2009-04-22
forum: Programming Talk
---

### Post by spdaniel91 on 2009-04-22
Hello,

Let's say I got:

```

char array[10];

array[2] = "Hello";
array[4] = "Hello2";
array[8] = "Hello3";


```

How can I make a loop iterating only on those non-empty entries?

---

### Post by namegame on 2009-04-22
I'll try to point you towards a solution but not do it for you. :)

All of your "non-empty" entries share a common factor, the index of all of your non-empty entries is even. Think about how you could incorporate that into your loop.

---

### Post by spdaniel91 on 2009-04-22
XD

Actually, I was just giving it as an example. I'm trying to make a prime number generator, and I have an array that contains all of the prime numbers found. To check if a number is prime, I have to loop into all of the prime numbers that are smaller than it.

By the way, the array contains integrers, so I can't do 

```
if(plist[i] != "")
```

---

### Post by tneva82 on 2009-04-22
> **spdaniel91 said:**
> XD

Actually, I was just giving it as an example. I'm trying to make a prime number generator, and I have an array that contains all of the prime numbers found. To check if a number is prime, I have to loop into all of the prime numbers that are smaller than it.

By the way, the array contains integrers, so I can't do 

```
if(plist[i] != "")
```

Howabout put something like -1 to "empty" points and checking wether number is <0?

Not sure is there even such a thing as empty int value in array that is defined(and not undefined randomg garbage).

---

### Post by dwhitney67 on 2009-04-22
> **spdaniel91 said:**
> Hello,

Let's say I got:

```

char array[10];

array[2] = "Hello";
array[4] = "Hello2";
array[8] = "Hello3";


```

How can I make a loop iterating only on those non-empty entries?

Why are you writing code like this?  The assignments are not compatible.  You are attempting to assign a const char* (i.e. a "string") to a single char, and doing it three times in the example above.

---

