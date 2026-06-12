---
title: "Python - Print numbers without making a list?"
date: 2009-03-23
forum: Programming Talk
---

### Post by dodle on 2009-03-23
In python, if I wanted to print a list of numbers I could make a list then print it:[PHP]list = [1,2,3,4,5,6,7,8,9,10]
print list[/PHP]or:[PHP]list = [1,2,3,4,5,6,7,8,9,10]
for num in list:
	print num[/PHP]But if I wanted to print out the numbers 1-10 without making a list, how would I do it?

---

### Post by ghostdog74 on 2009-03-23
range()

---

### Post by lswest on 2009-03-23
Yeah, you could just do that with:

[PHP]for x in range(1,11):
    print x
[/PHP]

Range is a function that reads from one position up to (but not including) the last position specified in the function (thus 1,11=1-10)

---

### Post by dodle on 2009-03-23
Thank you, very helpful.

---

### Post by ghostdog74 on 2009-03-23
> **lswest said:**
> Yeah, you could just do that with:

[PHP]for x in range(1,11):
    print x
[/PHP]
for the sole purpose of just printing a range out, just print range(1,11) will do. No need for a loop.

---

### Post by lswest on 2009-03-23
> **ghostdog74 said:**
> for the sole purpose of just printing a range out, just print range(1,11) will do. No need for a loop.

Always useful to know (I've not been doing python for all too long), thanks for the info.

---

### Post by wmcbrine on 2009-03-23
In Python 2.x, range() returns a list, so technically it doesn't fulfill the OP's stated requirement of "without making a list" (although it does what he really wanted). But xrange() returns an iterator, so it does.

In Python 3.x, xrange() becomes range(), and the old range() is dead.

---

