---
title: "Changing 1 dictionary seems to change another one. Why?!"
date: 2010-02-20
forum: Programming Talk
---

### Post by MadnessRed on 2010-02-20
Hi,I have this code

>>> a = {}
>>> print a
{}
>>> b = a
>>> b[0] = 1
>>> print a
{0: 1}

But I dont understand, I didn't do anything to a so why has it changed? I then tried the copy function

>>> c = {}
>>> print c
{}
>>> d = c.copy()
>>> d[0] = 1
>>> print c
{}
>>> print d
{0: 1}

So why does this happen, its bizarre.
Its the same with lists.

But not with strings or numbers

---

### Post by MadnessRed on 2010-02-20
delete please, posted in wrong topic

---

### Post by Some Penguin on 2010-02-20
Wouldn't surprise me if Python (which I suspect that is, but have never used personally) makes a distinction between references and primitive types.

i.e.


a = b

where b is a reference to a complex object (such as a list, or dictionary / associative array) just copies the reference; in other words, a and b refer to the same object, and therefore changes to the underlying object are visible to both.

This is supported by the existence of an explicit copy() method, which presumably serves as a copy constructor (create a new object of the same type with the same contents -- I couldn't tell you whether it deep-copies any contents which happen to be complex types or just uses the same references, however -- the odds are probably in favor of the latter).

---

### Post by CptPicard on 2010-02-20
You need to think in terms of "values" and "bindings". A variable in Python is nothing but a label (a name) for some object -- the actual value. This means that what assignment does is that it binds the left-hand side symbol to the value that you get from the evaluation of the right hand side symbol. After that, both evaluate to the *same* object.

---

### Post by Bachstelze on 2010-02-20
> **MadnessRed said:**
> 
So why does this happen, its bizarre.
Its the same with lists.

To see exactly what happens, you can use the [font=monospace]id()[/font] function, which returns the address of an object in memory:

```

>>> a = [0, 1]
>>> id(a)
140449874664768
>>> b = a
>>> id(b)
140449874664768

```

As you can see, b and a are two names for the same object. If you want b to be a *copy* of a, and not a itself, you can do:

```
>>> a = [0, 1]
>>> id(a)
139640093633856
>>> b = a[:]
>>> b
[0, 1]
>>> id(b)
139640093705136

```

Here, b is a copy  of a, meaning that is is a totally different object (it doesn't have the same memory address), but contains the same elements. Now when I modify b:

```
>>> b[0] = 1
>>> b
[1, 1]
>>> a
[0, 1]

```

It doesn't modify a, because they are different objects.

---

### Post by MadnessRed on 2010-02-20
ok that makes sense, thanks for the fast responses.

But how come it doesn't happen with strings or integers

a = 1
b = a
b = 2
print a

outputs 1

---

### Post by CptPicard on 2010-02-20
In your example you first create a new integer, '1', and label that with 'a'. Then, you bind 'b' to the thing that 'a' is bound to, which is the same '1'. Next, you re-bind 'b' to a new integer, '2'. This has no bearing to what 'a' is bound to, which is still the same integer '1'.

---

### Post by MadnessRed on 2010-02-20
> **CptPicard said:**
> In your example you first create a new integer, '1', and label that with 'a'. Then, you bind 'b' to the thing that 'a' is bound to, which is the same '1'. Next, you re-bind 'b' to a new integer, '2'. This has no bearing to what 'a' is bound to, which is still the same integer '1'.

ok, so when I create a a variable, the name I give it simple "points" to that variable.

If however I point a variable to a constant eg 1. And try and copy it, then it cannot change the value or 1 so instead copies it.

thanks.

---

### Post by Bachstelze on 2010-02-20
> **MadnessRed said:**
> ok, so when I create a a variable, the name I give it simple "points" to that variable.

Not really. The name points to an *object in memory*. When you write

```
a = 1
```

you say "the name 'a' points to an object with the value 1". Now when you write

```
b = a
```

you say "the name 'b' points to the same object as name 'a'", which has the value 1. So when you will evaluate b, it will give 1. Now when you do

```
b = 2
```

you say, "the name 'b' now points to an object with the value 2", but *you did not change what 'a' points to*. 'b' will now evaluate to 2 but 'a' will still evaluate to 1.


With lists, it is different. When you write

```
a = [1, 2, 3]
```

it's the same thing as with integers, you say "the name 'a' points to an object with the value [1, 2, 3]". When you do

```
b = a
```

once again, it's the same, you say "the name 'b' points to the same object as name 'a'". But when you do

```
b[1] = 4
```

what you change is not what 'a' or 'b' points to, you change *an element of the object 'b' points to*, which is the same object 'a' points to. 'b' and 'a' still point to the same object, so they will always have the same value--[1, 4, 3]. If, howevr, you do

```
b = [1, 4, 3]
```

you say "'b' now points to an object with the value [1, 4, 3]". 'b' will evaluate to [1, 4, 3], but 'a' will still evaluate to [1, 2, 3], because this time you did not change what a points to.

---

### Post by The Cog on 2010-02-21
It helps to understand (I think) that even numbers are objects in python if you simply do:
>>> help(1)
after which you can do things like:
>>> a = 1
>>> a.__add__(1)
2
>>>

---

### Post by MadnessRed on 2010-02-23
> **Bachstelze said:**
> Not really. The name points to an *object in memory*. When you write

```
a = 1
```

you say "the name 'a' points to an object with the value 1". Now when you write

```
b = a
```

you say "the name 'b' points to the same object as name 'a'", which has the value 1. So when you will evaluate b, it will give 1. Now when you do

```
b = 2
```

you say, "the name 'b' now points to an object with the value 2", but *you did not change what 'a' points to*. 'b' will now evaluate to 2 but 'a' will still evaluate to 1.


With lists, it is different. When you write

```
a = [1, 2, 3]
```

it's the same thing as with integers, you say "the name 'a' points to an object with the value [1, 2, 3]". When you do

```
b = a
```

once again, it's the same, you say "the name 'b' points to the same object as name 'a'". But when you do

```
b[1] = 4
```

what you change is not what 'a' or 'b' points to, you change *an element of the object 'b' points to*, which is the same object 'a' points to. 'b' and 'a' still point to the same object, so they will always have the same value--[1, 4, 3]. If, howevr, you do

```
b = [1, 4, 3]
```

you say "'b' now points to an object with the value [1, 4, 3]". 'b' will evaluate to [1, 4, 3], but 'a' will still evaluate to [1, 2, 3], because this time you did not change what a points to.

ahh, that's makes sense :) thanks.

---

### Post by nvteighen on 2010-02-23
> **CptPicard said:**
> In your example you first create a new integer, '1', and label that with 'a'. Then, you bind 'b' to the thing that 'a' is bound to, which is the same '1'. Next, you re-bind 'b' to a new integer, '2'. This has no bearing to what 'a' is bound to, which is still the same integer '1'.

Sadly, Python doesn't work that way... what you say is what Python designers should have done and didn't :p 

Python makes a rather counter-intuitive and annoying distinction between mutable and immutable objects. Immutable objects are numbers (integers and floats), strings and tuples, while the rest are mutable (lists, custom classes, dictionaries, whatever). Immutable objects are passed **by value**, this means that when an object of this kind is used, a copy of it is created because it's its value which matters. Mutable objects, instead, are relevant considered as objects, not because of which their values are... so, they're passed **by reference**, which means what CptPicard said of "labels" assigned to single-existing objects.

---

