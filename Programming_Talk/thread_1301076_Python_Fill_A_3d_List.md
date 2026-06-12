---
title: "Python Fill A 3d List"
date: 2009-10-25
forum: Programming Talk
---

### Post by tdrusk on 2009-10-25
I am working on a program that uses the users input and creates a 3d list for the amount of input. For example:

a = ['u','b','u','n','t','u']

I want it to create an list using the length of array a like

```
b =[ 
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                [[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0],[0,0,0]],
                ]

```

How can I do this using lists and the len(a)?

---

### Post by Can+~ on 2009-10-25
[PHP]a = ['u','b','u','n','t','u'][/PHP]

First of all, why would you split a string into a list? A string already is iterable, and already has a __len__ method:

[PHP]a = "ubuntu"
n = len(a) # returns 6[/PHP]

Second, you can use multiplication:

[PHP]>>> [0]*5
[0, 0, 0, 0, 0]
[/PHP]

Therefore (I manually added some spacing, to make it easier to see):

[PHP]>>> [[[0]*3]*n]*n
[[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]]
[/PHP]

Why would you need a 3d-matrix? (Also, this isn't a matrix, it behaves like one, but in truth, is a list in a list in a list. If you want real matrices, use scipy)

---

### Post by tdrusk on 2009-10-25
> **Can+~ said:**
> [php]a = ['u','b','u','n','t','u'][/php]First of all, why would you split a string into a list? A string already is iterable, and already has a __len__ method:

[php]a = "ubuntu"
n = len(a) # returns 6[/php]Second, you can use multiplication:

[php]>>> [0]*5
[0, 0, 0, 0, 0]
[/php]Therefore (I manually added some spacing, to make it easier to see):

[php]>>> [[[0]*3]*n]*n
[[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]]
[/php]Why would you need a 3d-matrix? (Also, this isn't a matrix, it behaves like one, but in truth, is a list in a list in a list. If you want real matrices, use scipy)

My code is already written using a as an array and 3d list in mind. Right now the lengths of a and b are static, but I would like to make my program useful for other lengths.

---

### Post by diesch on 2009-10-25
> **Can+~ said:**
> 
[php]>>> [[[0]*3]*n]*n
[[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]], 
[[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]]
[/php]

Note that all this [0,0,0] are the same object - which is most likely not what one wants here:

```
>>> a=[[[0]*3]*n]*n
>>> a[0][0][0]=5
>>> a
[[[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]], [[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]], [[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]], [[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]], [[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]], [[5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0], [5, 0, 0]]]

```

---

### Post by diesch on 2009-10-25
> **tdrusk said:**
> My code is already written using a as an array and 3d list in mind. Right now the lengths of a and b are static, but I would like to make my program useful for other lengths.

Use numpy, see [http://www.scipy.org/Cookbook/BuildingArrays](http://www.scipy.org/Cookbook/BuildingArrays)

---

### Post by Can+~ on 2009-10-25
Diesch: You're right. I used the x*multiplier method when using numeral types, and I didn't think that it would copy references.

Here's a generator:

[PHP]makematrix = lambda n: [[[0,0,0] for a in xrange(0, n)] for b in xrange(0, n)]
makematrix(6)[/PHP]

---

### Post by tdrusk on 2009-10-25
> **Can+~ said:**
> Diesch: You're right. I used the x*multiplier method when using numeral types, and I didn't think that it would copy references.

Here's a generator:

[php]makematrix = lambda n: [[[0,0,0] for a in xrange(0, n)] for b in xrange(0, n)]
makematrix(6)[/php]
This worked.

Took me a minute to realize I had to set
b = makematrix(6)

Thanks!

---

