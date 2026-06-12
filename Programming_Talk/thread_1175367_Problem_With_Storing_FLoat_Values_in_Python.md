---
title: "Problem With Storing FLoat Values in Python"
date: 2009-06-01
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-06-01
Ey guys, I have a question. Here is my code:

```

def calcTrans(e):
	print e.pktLength, G.TransRate
        print '%.12f'%(e.pktLength/G.TransRate)
	return e.pktLength/G.TransRate

```
And here are the results:
```

961 1000000
0.000000000000

```

I am wondering why I am getting this as my result when the answer is obviously of float type. Any help greatly appreciated. Thanks in advance!

---

### Post by Habbit on 2009-06-01
If you are using Python 2.x and the types of both arguments is Integer, then the / operator performs an integer division, thus the truncation to 0. You can either convert one of the arguments to a floating point number or use the "future" statement to bring into scope the Python 3 division operator ("from __future__ import division") which always performs floating point division.

---

### Post by StunnerAlpha on 2009-06-01
Ah ok, yeah I changed one of the numbers to a decimal and it works. Thanks!

---

