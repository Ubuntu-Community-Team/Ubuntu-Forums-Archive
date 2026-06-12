---
title: "Multi-Dimensional Arrays in Python"
date: 2010-02-20
forum: Programming Talk
---

### Post by Penguin Guy on 2010-02-20
I've got a multidimensional array:
```

>>> rows = [
...          [ 1 , 2 , 3 ]
...          [ 4 , 5 , 6 ]
...          [ 7 , 8 , 9 ]
...        ]

```

And I want to make a link to it, but from a column point of view:
```

>>> columns = [
...             [ 1 , 4 , 7 ]
...             [ 2 , 5 , 8 ]
...             [ 3 , 6 , 9 ]
...           ]

```

So that if I change [COLOR="Green"]columns[/COLOR], it'll effect [COLOR="green"]rows[/COLOR]:
```
>>> columns[1][2] = 'Hello World!'
>>> print rows[2][1]
Hello World!
```


**The closest thing I could find was this:**
```

columns = map(list, zip(*rows))

```

---

### Post by Zugzwang on 2010-02-20
Such a "linking" between lists is, as far as I know, not a feature that Python supports. Rather, you would implement something like that in form of a class, which you probably have to write yourself. Some hints on that can be found here: [http://docs.python.org/reference/datamodel.html#emulating-container-types](http://docs.python.org/reference/datamodel.html#emulating-container-types)

---

### Post by avidday on 2010-02-20
numpy arrays support what I think you are trying to do:

```

In [1]: import numpy as np

In [2]: a=np.array([[0,1,2],[3,4,5]])

In [3]: b=a[:,1]

In [4]: print b
------> print(b)
[1 4]

In [5]: a[:,1]+=2

In [6]: print b
------> print(b)
[3 6]

```

---

### Post by raffaele181188 on 2010-02-20
[Tabular data]("http://pypi.python.org/pypi/tabular/0.0.8") may also help you :D

---

### Post by The Cog on 2010-02-21
Numpy matrix operations might also help:
```
>>> import numpy as np
>>> m=np.matrix([[1,2,3],[4,5,6],[7,8,9]])
>>> m
matrix([[1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]])
>>> m.transpose()
matrix([[1, 4, 7],
        [2, 5, 8],
        [3, 6, 9]])
>>> 

```

---

### Post by Penguin Guy on 2010-02-22
As I understand, the best solution would be to create a class - however classes are way to complicated for me so I settled for a function:

[PHP]
def flip(list):
    newList = []
    a = 0
    while a < len(list[0]):
        b = 0
        column = []
        while b < len(list):
            column.append(list[b][a])
            b += 1
        newList.append(column)
        a += 1
    return newList
[/PHP]

Thanks to everyone for all the help.

---

### Post by peevishone on 2010-06-02
> **Penguin Guy said:**
> I've got a multidimensional array:
```

>>> rows = [
...          [ 1 , 2 , 3 ]
...          [ 4 , 5 , 6 ]
...          [ 7 , 8 , 9 ]
...        ]

```And I want to make a link to it, but from a column point of view:
```

>>> columns = [
...             [ 1 , 4 , 7 ]
...             [ 2 , 5 , 8 ]
...             [ 3 , 6 , 9 ]
...           ]

```So that if I change [COLOR=Green]columns[/COLOR], it'll effect [COLOR=green]rows[/COLOR]:
```
>>> columns[1][2] = 'Hello World!'
>>> print rows[2][1]
Hello World!
```The closest thing I could find was [COLOR=Green]columns = zip(*rows)[/COLOR], but that doesn't help me since it doesn't link the two. Anyone know how I can do this?

   rows = [[ 1 , 2 , 3 ], [ 4 , 5 , 6 ], [ 7 , 8 , 9 ]]
  columns = [[ rows[0][0] , rows[1][0]  , rows[2][0]  ], [rows[0][1]  , rows[1][1] , rows[2][1]  ], [rows[0][2]  , rows[1][2]  , rows[2][2]  ]]

---

### Post by jpkotta on 2010-06-03
> **peevishone said:**
> rows = [[ 1 , 2 , 3 ], [ 4 , 5 , 6 ], [ 7 , 8 , 9 ]]
  columns = [[ rows[0][0] , rows[1][0]  , rows[2][0]  ], [rows[0][1]  , rows[1][1] , rows[2][1]  ], [rows[0][2]  , rows[1][2]  , rows[2][2]  ]]

But that doesn't do what OP wanted.  You need an extra layer of indirection.  The simplest way is to make the elements of the matrix 1 element lists.  

```

a = [[[1],[2]],[[3],[4]]]
b = [[a[0][0],a[1][0]],[a[0][1],a[1][1]]]
a[0][0][0] = 2

```
```

a: [[[2], [2]], [[3], [4]]]
b: [[[2], [3]], [[2], [4]]]

```
The correct way is to use something like numpy or roll your own class, as others have suggested.

---

### Post by Penguin Guy on 2010-06-03
I'm finished the project that I needed this for - the function I wrote worked just fine. But if someone could point me to a good example of a class similar to the one I'm looking for, I would be grateful - if only for educational purposes.

---

