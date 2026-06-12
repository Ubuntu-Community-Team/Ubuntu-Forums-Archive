---
title: "basic python"
date: 2011-06-08
forum: Programming Talk
---

### Post by scorpious on 2011-06-08
What does /= mean

context:
```
self.numerator /= gcd
```also the % sign
```
if x % i == 0:
```

---

### Post by BkkBonanza on 2011-06-08
self.numerator /= gcd

is the same as writing,

self.numerator = self.numerator / gcd
(where / is divide operator)

if x % i == 0:

the % operator is the modulus (short, mod) operator which returns the remainder of a division. when used like this equating 0 it's means that code will run every "i" times thru some situation. eg. x % 3 == 0 means every third time, assuming x is being incremented in a loop.  x divided by 3 with remainder being equal to 0, ie. 0,3,6,9 etc.

This syntax and terminology exists for many common languages not just python.

---

### Post by scorpious on 2011-06-08
So this function

```
def findgcd(12, 20):
    smaller = min(x, y)
    for i in range (smaller, 1, -1):
        if x % i == 0 and y % i == 0:
            return i
    return 1
```...will return 4 because 4 is divisible by 12 and 20 with no remainder?

---

### Post by nzjethro on 2011-06-08
Why do you have
> for i in range (smaller, 1, -1):
I'm new to Python, but I thought the "range" function had 2 parameters, a min and a max?
But yes, the "if" method will return 4, because it goes into 12 and 20 without remainder.

---

### Post by PeterP24 on 2011-06-08
Hi, 

@nzjethro : the range function can take an optional input (the step of the integer sequence) besides the ones you know (start and end - not necessarily min and max)

@scorpious: yes: 4 is chosen since it divides both x and y (12 and 20) without a remainder. I am not a programmer - but I remember about the Euclid algorithm to obtain the gcd - you may want to use it since it is more efficient than what you have (of course if you need it and you didn't placed that function in order to find some info about the % operator)

---

### Post by nzjethro on 2011-06-08
> @nzjethro : the range function can take an optional input (the step of the integer sequence) besides the ones you know (start and end - not necessarily min and max)

Thanks, I must try that at some stage.

---

### Post by BkkBonanza on 2011-06-08
If the Wikipedia entry for Euclid's algorithm is right then the recursive version looks pretty nice,
```

def findgcd(a, b):
  if b == 0:
    return a
  return findgcd(b, a % b)

```
(I think this assumes a > b but not entirely sure)

---

