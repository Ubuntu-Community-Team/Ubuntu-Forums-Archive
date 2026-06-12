---
title: "[Python numpy] Ambiguity with numerical type casting"
date: 2016-02-10
forum: Programming Talk
---

### Post by Erdaron on 2016-02-10
I ran into an issue where numpy's numerical types don't seem to be well-behaved. Consider the following sequence of commands:
[PHP]>>> type(np.uint64(5))
<type 'numpy.uint64'>
>>> type(np.uint64(5) + 5)
<type 'numpy.float64'>
>>> type(long(5))
<type 'long'>
>>> type(long(5) + 5)
<type 'long'>
>>> type(np.uint32(5) + 5)
<type 'numpy.int64'>
>>> type(np.int32(5) + 5)
<type 'numpy.int32'>
>>> type(np.int64(5) + 5)
<type 'numpy.int64'>[/PHP]

Basically, it seems that numpy's unsigned integer types get recast when mixed with native Python types. Unsigned 32-bit integer gets converted into signed 64-bit integer, and unsigned 64-bit integer into 64-bit float. Signed integer types are safe.

The latter conversion is of particular concern, because it can potentially wreck things.

Python 2.7.10 x64, numpy 1.10.4 x64 with MKL support (from Christoph Gohlke repo), on Windows 7 x64.

Am I missing some nuance here? Is there an order in which things get re-cast when mixed types are encountered?

---

### Post by Vaphell on 2016-02-10
> Basically, it seems that numpy's unsigned integer types get recast when mixed with native Python types. Unsigned 32-bit integer gets converted into signed 64-bit integer, and unsigned 64-bit integer into 64-bit float. Signed integer types are safe.

a quick research led me to this quick and dirty rule:

python int is int64.
if you mix unsigned types with it you get escalation to the int of higher width if possible to accomodate values outside their span, and if not (because already working with maximum width), promotion to float occurs as it has a bigger wingspan than int64 paid with the risk of precision loss.
I can't say that the logic behind it is rock solid (eg. max(uint32)+max(int64)>max(int64) ) but it's there.

```
>>> type(np.uint64(5) + 5)
<type 'numpy.float64'> 
```

signed + unsigned. Maximum width, escalation to int of higher order is impossible so float it is.

```
>>> type(np.uint32(5) + 5)
<type 'numpy.int64'>
```

uint32 + int64 = escalation to int64.

```
>>> type(np.int32(5) + 5)
<type 'numpy.int32'>
```

signed + signed = no escalation.


```
>>> type(np.int64(5) + 5)
<type 'numpy.int64'>  
```

same data type = no escalation.


Verdict: Don't mix yo types (implicitly)

---

### Post by Erdaron on 2016-02-16
Thank you for walking this reasoning all the way home for me. I think I've gotten lazy with type-checking in Python. This is a good lesson to be careful.

---

