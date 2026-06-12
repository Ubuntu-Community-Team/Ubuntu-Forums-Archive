---
title: "Float in Python?"
date: 2006-06-10
forum: Programming Talk
---

### Post by Kimm on 2006-06-10
I'm no Python programmet, but for a project I'm currently working on I need to use a float in Python.

I've been googling but I cant find anything I can make sence of. I found this:

f = float(<whatever calculation goes here>)
print f

Put if I do that with 1/10 I get: 0.0
Crealy wrong.

Could anyone help me out with this?

---

### Post by asimon on 2006-06-10
I am not into python myself, but if you compute 1/10 it's an integer calculation with the result an integer, i.e. 0. If you then convert that integer result to a float, then the end result is 0.0, makes perfect sense for me. You may want to use 1.0/10 to force a floating calculation, but then the result is a already a float and the float() call is not needed.

---

### Post by UbuWu on 2006-06-10
Try f = 1/10.0

---

### Post by Kimm on 2006-06-10
I got it working by calling:

from __future__ import division

But I believe the other solution would also work

---

### Post by Revert on 2006-06-10
"/" by itself will truncate if they're integers, so 1.0/10 would give the desired result.  Importing that package makes "/" return a decimal.

As an aside, in version 3.0 they're supposedly making "/" always return a remainder, and use "//", their floor division operator, for dividing with truncation.

Edited a typo

---

### Post by Kimm on 2006-06-10
Ok

I acctually cant use the "1.0/10" way, since this program must be completely theoretical...
I'll acctually have another program writing a Python script, executing it, and reading its output. I think that would be a quite efficient way of solving math problems.

#!/usr/bin/python

from __future__ import division

f = float(<problem>)
print f

---

### Post by Ubuntuud on 2006-06-11
1 / 10 = 0.1, but as an integer it's 0. So when you float it afterwards it returns 0.0.
How about "f = float(1)/10"?

---

### Post by angustia on 2006-06-18
it's a problem of writting.

if you put 1 and 10, python tries to guess the type of the numbers and both fall into "int", so when dividing two "int", python uses integer division (div) (solving 1/10 gives you 0 integers)

when you write a number with a .0, it falls to float so python uses float division (fdiv) and you get the number with all its decimals.

---

