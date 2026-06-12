---
title: "Python: List vs Tuple?"
date: 2011-06-14
forum: Programming Talk
---

### Post by kevin11951 on 2011-06-14
Let's assume I simply need a list of values to use in a for loop.

In terms of speed: List or Tuple?

---

### Post by Barrucadu on 2011-06-14
```
barrucadu on randolph in ~/tmp [branch: master]
 >>>  uname -a; python -V
Linux randolph 2.6.39-ARCH #1 SMP PREEMPT Fri May 20 11:33:59 CEST 2011 x86_64 Intel(R) Atom(TM) CPU N450 @ 1.66GHz GenuineIntel GNU/Linux
Python 3.2
```

```
barrucadu on randolph in ~/tmp [branch: master]
 >>>  cat test-list.py; time python test-list.py; time python test-list.py; time python test-list.py
foo = list (range (0, 1000000))

for i in foo:
    i * 2
Real: 1.22s User: 1.10s System: 0.12s Percent: 99% Cmd: python test-list.py
Real: 1.28s User: 1.15s System: 0.10s Percent: 97% Cmd: python test-list.py
Real: 1.23s User: 1.10s System: 0.11s Percent: 98% Cmd: python test-list.py
```

```
barrucadu on randolph in ~/tmp [branch: master]
 >>>  cat test-tuple.py; time python test-tuple.py; time python test-tuple.py; time python test-tuple.py
foo = tuple (range (0, 1000000))

for i in foo:
    i * 2
Real: 1.23s User: 1.14s System: 0.09s Percent: 99% Cmd: python test-tuple.py
Real: 1.27s User: 1.18s System: 0.09s Percent: 99% Cmd: python test-tuple.py
Real: 1.26s User: 1.16s System: 0.09s Percent: 98% Cmd: python test-tuple.py
```

Doesn't seem to be much difference.

---

### Post by TwoEars on 2011-06-14
Well, it should never come to do speed, it should come down to the fact of whether or not you need a mutable group of values. If you need speed so much that you would consider using different object types, then perhaps Python isn't the language for you.

Anyway, the difference is beyond minute - and it depends on many many things, so it's hard to give you a solid answer. The major difference is the memory usage. Tuples will use less memory.

---

### Post by simeon87 on 2011-06-14
Rewrite that code in C. That's the fastest you can do.

At first I assumed tuple would be faster as they are immutable but as the above profiling has shown, there's not much difference. That also makes sense actually because when both data types are constructed, the differences in bookkeeping and mutability don't really matter.

---

### Post by Barrucadu on 2011-06-14
I haven't confirmed this, but I wouldn't at all be surprised if internally tuples and lists were implemented using the same data structures and algorithms.

---

### Post by nvteighen on 2011-06-14
The only difference there might be is that lists, being mutable, won't be optimized as tuples could instead. Tuples are guarranteed to never change, so you can assume that in order to optimize code; you just can't assume that for lists, or at least not in the same extent that you can for tuples.

---

