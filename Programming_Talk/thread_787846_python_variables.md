---
title: "python variables"
date: 2008-05-09
forum: Programming Talk
---

### Post by Jacks0n on 2008-05-09
Hi,

I'm making a game in python where there's a variable called self.game._game which stores the game state as a list. And I want to be able to save it (assign another variable to it), change it, and be able to refer to the old state. But in python if you assign a new variable to another one, it seems to make a pointer and not copy it's data.

eg..

```

a = [1,2,3,4]
b = a
a.append(5)
print b
>>> [1,2,3,4,5]

```

So how are you supposed to save the state of a variable, where if you change it later, the variable you originally assigned it to doesn't also change?

- Thanks, Jackson

---

### Post by LaRoza on 2008-05-09
Do you plan an changing the old state?

You can save a copy of it as a tuple, which would ensure it wouldn't change.

```

a = [1,2,3,4]
copya = tuple(a)
b = a
# copya cannot be changed and has the same elements as a when it was made. 
# If you do for some reason want to change it, you can convert it to a list

```

---

### Post by Ann.A on 2008-05-09
another way to think about it could be:

```

a = [1, 2, 3, 4]
b = []
b.extend(a)
a.append(5)
print b

``` 

b would print [1, 2, 3, 4]

---

### Post by WW on 2008-05-09
Does the list contain lists or other nontrivial data elements?  If so, you may need a deep copy.

Here is a simple copy, similar to LaRoza's suggestion:
```

>>> a = [1,2,3,4]
>>> b = list(a)
>>> a.append(5)
>>> b
[1, 2, 3, 4]
>>> 

```
However, even with **tuple** instead of **list**, it might not work the way you expect.  For example,
```

>>> x = [1,2,3]
>>> y = [4,5]
>>> a = [x,y]
>>> b = tuple(a)
>>> b
([1, 2, 3], [4, 5])
>>> y.append(6)
>>> b
([1, 2, 3], [4, 5, 6])
>>> 

```
Note that b reflects the change in y.

You can use [deepcopy](http://docs.python.org/lib/module-copy.html) to avoid this:
```

>>> import copy
>>> x = [1,2,3]
>>> y = [4,5]
>>> a = [x,y]
>>> b = copy.deepcopy(a)
>>> b
[[1, 2, 3], [4, 5]]
>>> y.append(6)
>>> a
[[1, 2, 3], [4, 5, 6]]
>>> b
[[1, 2, 3], [4, 5]]
>>> 

```
In this case, b is a completely separate copy.

---

### Post by Jacks0n on 2008-05-09
Oh ok, cool. Thanks! I never realized python did this until writing the game. It took me a while to figure out that it made the changes in both variables.

Edit: The variable was 9 sub-lists within a list, and it turns out I needed to use the copy.deepcopy() method.

- Thanks, Jackson

---

### Post by ghostdog74 on 2008-05-09
you can do shallow copy
```

b=[1,2,3,4]
c=b[:]


```

---

### Post by raddmadd on 2008-05-09
When you create a variable, it is linked to the object you originally created it with.

So, thus,

```

variable = object

```

what you did is:
```

variable1 = object1
variable2 = variable1

```

object1 exists in memory.  variable1's name is used and references to object1.  But, since variable2's name is referenced to variable1, it is then not referencing to variable1, but rather object1.

When you assign variable1 to a new object, it will not change object1, but rather create a new object.  Python uses reference counts, so that objects will not be deleted until there are no more variables referencing that object (when the reference count hits 0.  Although some commonly used objects have a reference count greater than the amount of variables referencing to it, for speed.  So that Python doesn't have to recreate it every time.)

So, you can think of this:
```

variable1 = object1
variable2 = variable1

```

As, this:
```

variable1 = object1
variable2 = object1

```

Also, understand immutability (objects that can't be changed) and mutability (objects that can be changed.)

strings, numbers, and tuples are immutable
lists and dictionaries are mutable. 

For instance, try:
```

a = "raddmadd is coolz"
a[12] = "r"

```

You'll get an error.  I could do this, though:
```

a = "raddmadd is coolz"
a[12:17] = "rulez"

```

But a[12:17] simply creates a new object, not changes the object originally signed to variable a.

Well, that was fun.  I'm bored in school so that's why I gave my input, hehe. :P

---

### Post by chelom on 2009-09-15
well u can use list comprehension for example u have
[FONT=monospace]a=[1,2,3]
u have make a exact copy of "a" without refering to it for example
b=[k for k in a]
then b will be a exact copy of a.

>>>a=[1,2,3]
>>>b=[k for k in a]
>>>b
[1,2,3]
>>>a.append(4)
b, a
[1,2,3], [1,2,3,4] 
[/FONT]

---

### Post by nvteighen on 2009-09-15
> **chelom said:**
> well u can use list comprehension for example u have
[FONT=monospace]a=[1,2,3]
u have make a exact copy of "a" without refering to it for example
b=[k for k in a]
then b will be a exact copy of a.

>>>a=[1,2,3]
>>>b=[k for k in a]
>>>b
[1,2,3]
>>>a.append(4)
b, a
[1,2,3], [1,2,3,4] 
[/FONT]

But, actually the best is to use the copy module... Ok, a simple list may be copied by using that simple method, but what if you're dealing with a n-dimensional matrix?

---

