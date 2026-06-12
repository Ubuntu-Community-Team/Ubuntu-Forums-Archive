---
title: "Pythonic way to convert data in list or tuple"
date: 2010-11-03
forum: Programming Talk
---

### Post by MicahCarrick on 2010-11-03
Hey y'all. What's the pythonic way of running each element of a list or tuple through the same function? For example, I have a list of bytes and I want to turn each one into an ascii character using chr()

```
for value in tempdata:
    data += chr(value)
```

---

### Post by MicahCarrick on 2010-11-03
Just found the map() function.

---

### Post by meastwood on 2010-11-03
Am no expert but this is one way -

```
>>> a=[97, 98, 99, 100]
>>> [ chr(b) for b in a ]
['a', 'b', 'c', 'd']

>>> res=[ chr(b) for b in a ]
>>> res
['a', 'b', 'c', 'd']
```

---

### Post by mo.reina on 2010-11-03
> **meastwood said:**
> Am no expert but this is one way -

```
>>> a=[97, 98, 99, 100]
>>> [ chr(b) for b in a ]
['a', 'b', 'c', 'd']

>>> res=[ chr(b) for b in a ]
>>> res
['a', 'b', 'c', 'd']
```

+ 1 

i feel that list comprehensions are underused and that not enough people know about them.

map is probably the shortest way to do what you want though.

---

### Post by schauerlich on 2010-11-03
> **mo.reina said:**
> + 1 

i feel that list comprehensions are underused and that not enough people know about them.

map is probably the shortest way to do what you want though.

List comprehensions are just syntactic sugar over map() and filter(). :) But I agree, they're underused and much easier to read for those not used to these crazy lambda things, or functional programming in general.

---

### Post by tauman5263 on 2010-11-03
I would use a list comprehension. A generator expression would be better for very large list (or if you only need to iterate over the list once), IMO.

Here's some more info on the subject:
[http://wiki.python.org/moin/PythonSpeed/PerformanceTips#Loops]("Loop Performance")

BTW, dict comprehensions are pretty neat if you are using Python 2.7+.

---

