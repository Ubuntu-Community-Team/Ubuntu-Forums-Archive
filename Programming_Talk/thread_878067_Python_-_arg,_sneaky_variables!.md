---
title: "Python - arg, sneaky variables!"
date: 2008-08-02
forum: Programming Talk
---

### Post by Erdaron on 2008-08-02
There is something about Python variable declarations that keeps catching me off-guard.

In particular, when you make one list equal to another, then alter the first list, and that alters the second list.
[PHP]>>> a = range(10)
>>> b = a
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> a[4] = 15
>>> a
[0, 1, 2, 3, 15, 5, 6, 7, 8, 9]
>>> b
[0, 1, 2, 3, 15, 5, 6, 7, 8, 9][/PHP]

However, this only works when altering a specific member of the list. Well, sort of. If you got through the list one by one, this does not happen.

[php]>>> a = range(10)
>>> b = []
>>> for i in range(10):
	b.append(a[i])

>>> a[4] = 0
>>> a
[0, 1, 2, 3, 0, 5, 6, 7, 8, 9]
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> [/php]

If you alter the entire list, this also doesn't work.

[PHP]>>> a = range(10)
>>> b = a
>>> a = 2
>>> a
2
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> [/PHP]

Using [:] is supposed to ensure variables are cloned, but that doesn't work on multi-dimensional arrays.

[php]>>> a = [range(5),range(5)]
>>> b = a[:]
>>> a[0][4] = 10
>>> b
[[0, 1, 2, 3, 10], [0, 1, 2, 3, 4]][/php]

Individual variables seem to be created with independence, like whole lists.

This seems like an inconsistent application of rules. If declaration a = b creates two variables pointing to the same memory location, that should either always be the case or never.

Am I justified in my frustration? I realize that this behavior can probably be used for some neato tricks, but for someone just starting this can be a really infuriating surprise. Especially since it is not mentioned in the tutorial part of the docs.

Is there a greater purpose to this that I'm not realizing, and later on I will be thankful for this functionality?

---

### Post by tamoneya on 2008-08-02
in the first example you make one array and point "a" at it.  Then you point "b" at what "a" is pointing at.  This differs from the second example where you make and array and point "a" it.  Then you make another array(empty) and point "b" at it.  Then you take the values in the array pointed to by "a" and put them into the array pointed to by "b".  The difference is that there are two physical arrays in memory in the second example ( you used "[]" twice since range uses "[]").  

The third exampe you make and array "a" and point "b" at it and then you leave "b" pointing to the array and you point "a" to a number.  You never repointed "b" though.

---

### Post by Wybiral on 2008-08-02
You're confusing labels with objects. "a" is nothing but a reference to an object, so saying "a = 5" doesn't change the previous object that "a" was a reference to, it just makes "a" reference something else.

What you really need to understand is that accessing an array is just calling a method on an object, for instance "x[0] = 1" is really just "x.__setitem__(0, 1)"

Everything in Python is a reference, the main difference is that most things (like strings and numbers) are immutable meaning they can't change (so you don't have issues with side-effect like this).

If you want to copy an entire list of lists (creating a new object, independent from the previous) use the [copy module]("http://docs.python.org/lib/module-copy.html").

---

### Post by Erdaron on 2008-08-02
But all of those cases use the same operator, =. 

In the second case, I could argue that b.append(a[j]) should point the newest member of b to a[j] instead of allocating new memory and filling it with value of a[j].

[quote=tamoneya]in the first example you make one array and point "a" at it. Then you point "b" at what "a" is pointing at.[/quote]
[quote=tamoneya]The third exampe you make and array "a" and point "b" at it and then you leave "b" pointing to the array and you point "a" to a number. You never repointed "b" though.[/quote]
This doesn't make sense to me. Syntax is identical in the two cases. I didn't do anything special to leave b pointing someplace.

I'm sorry if I sound combative. This situation has caused me to lose several hours of work. I kept thinking I made a mistake in my program somewhere, or had corrupt files or something, because I kept getting absolute garbage.

---

### Post by Wybiral on 2008-08-02
> **Erdaron said:**
> But all of those cases use the same operator, =. 

In the second case, I could argue that b.append(a[j]) should point the newest member of b to a[j] instead of allocating new memory and filling it with value of a[j].

That is exactly what happens... The difference is that you're probably assuming "a[j]" to be an immutable object so you have the illusion that it's new because it can't be altered. If "a[j]" were a list or dict or something, it would, in fact, be the same object.

If it helps you understand this better, know that integers are immutable, think about this:
```

x = 1
x = 2

```
Do you really think you can change the value of the number "1" to "2"? That would be illogical...
```

x = 1
x += 2

```
This is just sugar for saying "x = x + 2", which is not altering the object "1"... It's immutable.

Lists, on the other hand, are mutable.

---

### Post by pmasiar on 2008-08-02
> **Erdaron said:**
> But all of those cases use the same operator, =. 

Operator = binds name on left with object on right.

First example, names a and b pointed to the exactly same object. 

In 2nd example, you build list from empty, so obviously they were different, even if they happens to have same values.

3rd example, you reassigned a to 2, but b kept the old value (nobody changed it).

a[:] creates a slice, resulting in the copy of values, but your was seemingly not deep enough :-) There is deepcopy utility which copies multilevel structures, your was 2D: list of (references to) lists.

> If declaration a = b creates two variables pointing to the same memory location, that should either always be the case or never.

First, = is not declaration, but statement: assignment statement. It does not point to memory location, but to an object (which has memory location, but also other attributes).

'a = b' creates yet another name ('a') to the object currently accessible via name 'b'.

@Wybiral: you confuse 'label' with 'variable name'. 'Label' is target for GOTO. You never used GOTO, but still, that usage is reserved :-)

---

### Post by Erdaron on 2008-08-02
I think my understanding was too thin here; thank you all for patiently explaining this to me. I'm still chewing on it.

So if I may carry this further. What's the difference between shallow and deep copy?

Shallow copy does exactly what's been messing me up - crates references to data being copied, while deepcopy actually creates complete new variables filled with the exact same information, but not linked to the original? Is this right?

---

### Post by pmasiar on 2008-08-02
> **Erdaron said:**
> What's the difference between shallow and deep copy?

[http://en.wikipedia.org/wiki/Deep_copy](http://en.wikipedia.org/wiki/Deep_copy) :-)

---

### Post by pmasiar on 2008-08-04
[Undestanding  Python variables](http://starship.python.net/crew/mwh/hacks/objectthink.html) and references (by Alex Martelli), and also [Python Objects](http://effbot.org/zone/python-objects.htm) - explained by another Python superexpert, Fredrik Lundh

---

