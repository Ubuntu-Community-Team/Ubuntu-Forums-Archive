---
title: "Array in python"
date: 2009-01-14
forum: Programming Talk
---

### Post by adamsnative on 2009-01-14
how do i manipulate 2d array in python as doni in c/Java using nested for loops 
Plz help with an example

---

### Post by chronographer on 2009-01-14
In python an array is usually referred to as a list. it is created with square brackets '[' and ']' you can also have other things like dictionaries and tuples.

get a book ('learning python' is a good one) or read the online documentation (it is excellent)

some examples:

an_array = []
an_array.append(1)
print an_array
#[1]
an_array2=[1,2,5,4,1,3,5,9]
for i in an_array2:
    print "the number is: ", i
#the number is: 1
#the number is: 2
#the number is: 5
...


its really easy. Search google for more. like this: 
[http://pentangle.net/python/handbook/node39.html](http://pentangle.net/python/handbook/node39.html)
or this:
[http://www.secnetix.de/olli/Python/list_comprehensions.hawk](http://www.secnetix.de/olli/Python/list_comprehensions.hawk)

p.s. you can have arrays of arrays, and arrays of arrays of arrays ad infinitum... eg:

>>> a = [1,2,3]
>>> b = [3,2,1]
>>> c = [a,b]
>>> print c
[[1, 2, 3], [3, 2, 1]]
>>> d = [b,a]
>>> e = [c,d]
>>> print e
[[[1, 2, 3], [3, 2, 1]], [[3, 2, 1], [1, 2, 3]]]

---

### Post by kimberly2380 on 2009-01-15
thanks for your explanation the link given...it is useful

---

### Post by Wybiral on 2009-01-15
Alot of the time, it will save you a ton of code to use use a dict with a tuple key...
```

grid = {}
grid[0, 0] = 1
grid[0, 3] = 2
print grid[0, 0]
print grid[0, 3]

# which makes it easier to do things like...
position = (0, 3)
print grid[position]

```

---

### Post by iQuizzle on 2009-01-15
if you're doing any sort of numerical stuff i'd recommend getting the numpy package.

sudo apt-get install python-numpy

---

### Post by adamsnative on 2009-01-21
Thanks for all ur help i have learned a lot

---

### Post by Tony Flury on 2009-01-21
One warning about python (compared to other languages) is the way it builds lists - if you build lists from other objects (as a short hand for lots of initialisation code : 

```

a = [0,0]
b = [a,a]
# instead of writing b=[[0,0],[0,0]]

```
In the above code b is a lists of lists, and b[0] and b[1] are exactly the same object, they are not copies.

so if you then do 
```

a[0]=1

```
b will now be equal to [[1,0],[1,0]]. This can be undesirable and unexpected in many cases.

also
```

b[0][1] = 2

```
will now result in b = [[0,2],[0,2]] because again you changed a (although not explicitly), again potentially an unexpected outcome

There is a deepcopy method that takes a copy of the values (and not a reference) that can be used to avoid these gotchas, or initialise using literals and a simple list constructor

```

>>> a = [0,1]
>>> b = [a,a]
>>> a[1]=2
>>> print b
[[0, 2], [0, 2]]
>>> a[0]=1
>>> print b
[[1, 2], [1, 2]]
>>> b[0][1]=3
>>> print b
[[1, 3], [1, 3]]
>>> print a
[1, 3]
# Demonstrate Deepcopy
>>> import copy
>>> b = [copy.deepcopy(a), copy.deepcopy(a)]
>>> print b
[[1, 3], [1, 3]]
>>> a[0]=0
>>> print b
[[1, 3], [1, 3]]
>>> b[1][0] = 4
>>> print b
[[1, 3], [4, 3]]
>>> print a
[0,3]

```
Using deepcopy means that the b[0] and b[1] are seperate objects, but the initialisation of b is now a lot more code.

---

