---
title: "Bitwise Operators and other things in Python"
date: 2010-08-11
forum: Programming Talk
---

### Post by err1100 on 2010-08-11
Hello all - 

I've been coding in Python for a couple of months now, and I recently ran across the following piece of code (where x is a set or list):

```
f = lambda x: [[y for j, y in enumerate(x) if (i >> j) & 1] for i in range(2**len(x))]
```

I was hoping someone could explain to me the following components:

1. 'y for j': after doing some reading, I think I understand the basic principles of * for *, but I still don't think I get exactly what Python is doing.

2. '(i >> j) & 1': I read something somewhere about shifting with '>>', but quite frankly, I'm still completely clueless. Also, I'm very new to bitwise operators and could use some explanation.

Thanks,
err1100

---

### Post by schauerlich on 2010-08-12
> **err1100 said:**
> 1. 'y for j': after doing some reading, I think I understand the basic principles of * for *, but I still don't think I get exactly what Python is doing.

It's a nested list comprehension.

[http://docs.python.org/tutorial/datastructures.html#list-comprehensions](http://docs.python.org/tutorial/datastructures.html#list-comprehensions)

```
mylist = [2*x+1 for x in range(10)]
```

Is equivalent to

```
mylist = []
for x in range(10):
    mylist.append(2*x+1)

```

See the docs page for more details.

Here's a "translation" if it helps:

```
f = lambda x: [[y for j, y in enumerate(x) if (i >> j) & 1] for i in range(2**len(x))]
```

```
def f(x):
     mylist = []
     for i in range(2**len(x)):
             for j, y in enumerate(x):
                     if (i >> j) & 1:
                             mylist.append(y)
     return mylist
```


> 2. '(i >> j) & 1': I read something somewhere about shifting with '>>', but quite frankly, I'm still completely clueless. Also, I'm very new to bitwise operators and could use some explanation.

[http://en.wikipedia.org/wiki/Bitwise_operators](http://en.wikipedia.org/wiki/Bitwise_operators)

Basically, you shift all of the bits over one direction or the other. It's like multiplying or dividing by a power of 2. & does a bitwise AND operation on each bit, with 1 being True and 0 being False.

---

### Post by Lootbox on 2010-08-12
> **err1100 said:**
> 2. '(i >> j) & 1': I read something somewhere about shifting with '>>', but quite frankly, I'm still completely clueless. Also, I'm very new to bitwise operators and could use some explanation.

(i >> j) means shift the bitwise representation of i to the right j times. 0 bits fill in the space on the left. For example, 37 >> 2 would evaluate to:

00100101 => 00001001

...which is 9 in decimal (equivalent to dividing by 2^2 and throwing out the fractional component).

The & operator lines up the bitwise representation of the two arguments and compares pairs of bits at a time. It treats 0 as false and 1 as true and performs the equivalent of the boolean && (so if both are 1, the result is 1; 0 otherwise).

So if I had 177 & 157 (177 is 10110001, 157 is 10011101):

```

10110001
10011101
--------
10010001

```

The result is 10010001, which is 145.

Since the bitwise representation of 1 is just a bunch of zeros and a 1 in the right-most spot, (i >> j) & 1 has the equivalent effect of yielding i's j-th bit from the right.

---

### Post by schauerlich on 2010-08-12
> **Lootbox said:**
> (i >> j) means shift the bitwise representation of i to the right j times. 0 bits fill in the space on the left.

Nope, it's filled in by the sign bit.

---

### Post by Lootbox on 2010-08-12
> **schauerlich said:**
> Nope, it's filled in by the sign bit.

Ah, my bad. Is there an unsigned shift operator in Python?

---

### Post by trent.josephsen on 2010-08-12
Python doesn't have any unsigned types, and ints don't roll over, so a right-shift operator that filled in zeros unconditionally would be pointless.  If you would use an unsigned type for it, just make it positive.

---

