---
title: "Data type multiple children; randomized allocation"
date: 2013-04-26
forum: Programming Talk
---

### Post by kumoshk on 2013-04-26
I'm programming in Python, firstly.

So, I have a class that I made. Each class has a number value. It has both multiple parents and multiple children, and add and subtract methods. When you add/take away from the children, it'll add/take away from the parents, too. That's not a big problem. However, when you take away from the object, I need some algorithms to determine which children to take from, and how much to take away from each.

The number values are fractions.Fraction objects, for arbitrary precision.

I'd like one that selects a random assortment that's at least semi-efficient and elegant.

This is problematic because while it may select a random number from the first item, it doesn't yet know if there'll be enough in the later items; so, it may have to come around again, and you won't know how much you'll have to work with in each item, so if it tries too high, it may have to try an arbitrary lower number next time (since we're dealing with fractions and just looping through by adding or subtracting one every time won't work so well).

Any ideas? Are there already classes like this available for use?

---

### Post by Vaphell on 2013-04-26
if you want to randomly select subgroups, look at itertools
[http://docs.python.org/2/library/itertools.html](http://docs.python.org/2/library/itertools.html)
at the bottom of the page there are examples how to get random product/permutation/combination


determining maximum allowed substraction should be easy (minimum of all values)

```
>>> class A:
...   def __init__( self, val ):
...     self.value = val
... 
>>> objs = [ A(12), A(4), A(10), A(3) ]
>>> print min( x.value for x in objs )
3
```

---

