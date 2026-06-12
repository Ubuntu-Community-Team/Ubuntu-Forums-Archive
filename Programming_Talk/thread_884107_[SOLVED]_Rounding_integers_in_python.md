---
title: "[SOLVED] Rounding integers in python"
date: 2008-08-08
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-08
How can I round an integer in python? *Not decimal, an integer!*
I want to round an integer, like 185, with precision of 40. How to do it? 

Thanks for your help.

---

### Post by Lster on 2008-08-08
Something *like*:

[PHP]
def roundto(x, n):
	a = x/n
	b = a+1
	a *= n
	b *= n
	
	if x-a < b-x: return a
	return b


print roundto(100, 30)
[/PHP]

You should test it gives you all the right answers depending on the numbers you enter. For example, check if it rounds borderline cases as you want. And check that it rounds negative numbers OK.

---

### Post by mssever on 2008-08-08
Surely Python has rounding functions already.

---

### Post by days_of_ruin on 2008-08-08
> **mssever said:**
> Surely Python has rounding functions already.

Correct. ```
>>>a = round(10.3)
>>>print a
10.0
```

Do ```
>>>help(round)
```
for more info

---

### Post by geirha on 2008-08-08
The builtin round method only rounds to powers of ten ...

```
>>> roundint= lambda n,p: (n+p/2)/p*p
>>> roundint(185,40)
200
>>> roundint(179,40)
160
>>> roundint(180,40)
200

```

---

### Post by samjh on 2008-08-08
There are many many ways to round integers.

Here's a naive implementation, using symmetrical arithmetic rounding (ie. half-round-up, with "up" for negative numbers becoming more negative), the sort of rounding they teach in junior maths classes:
```
def iround(val, step):
	halfstep = step / 2.0
	if val >= 0:
		remainder = val % step
		if remainder < halfstep:
			result = val - remainder
		else:
			result = val - remainder + step
	else:
		val *= -1
		remainder = val % step
		if remainder < halfstep:
			result = -1 * (val - remainder)
		else:
			result = -1 * (val - remainder + step)
	return result
```

---

### Post by ghostdog74 on 2008-08-08
```

>>> import math
>>> math.floor(10.3+0.5)
10.0

```

---

### Post by Ed J on 2008-08-08
```
>>> round(1234, -2)
1200.0
>>> round(1234, -3)
1000.0
>>> round(1234, -1)
1230.0

```

Oh, I just saw the precision of 40 part.

---

### Post by crazyfuturamanoob on 2008-08-09
Ok, Thanks. Thanks to all Im too lazy to test those. I'll just use geirha's way. It looks simple and works.

---

### Post by days_of_ruin on 2008-08-09
By precision of 40 you mean upto 40 digits to the right of
the decimal point?Use round(number,40).Nothing is simpler than that.
Reimplementing rounding number in python will most likely be slower
because round is probably written in C.

---

### Post by samjh on 2008-08-09
> **days_of_ruin said:**
> By precision of 40 you mean upto 40 digits to the right of
the decimal point?

I think he means to round to the nearest 40.

---

### Post by crazyfuturamanoob on 2008-08-09
> **samjh said:**
> I think he means to round to the nearest 40.
Thats the point. ;) But its solved already.

---

