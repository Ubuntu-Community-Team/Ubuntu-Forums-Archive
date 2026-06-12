---
title: "a little numpy/python enigma"
date: 2010-06-11
forum: Programming Talk
---

### Post by stair314 on 2010-06-11
Anyone have an explanation for this?

>>> import numpy
>>> a = numpy.zeros((2,2))
>>> id(a[0,1])
27336416
>>> id(a[0,0])
26966160
>>> 27336416-26966160
370256
>>> id(a[0,1])-id(a[0,0])
0

---

### Post by Tony Flury on 2010-06-11
interestingly - on my version of python 2.5.2 - the two ids are the same.

[PHP]
>>> import numpy
>>> a = numpy.zeros((2,2))
>>> a
array([[ 0.,  0.],
       [ 0.,  0.]])
>>> id(a[0,1])
139961696
>>> id(a[0,0])
139961696
>>> id(a[0,0]) - id(a[0,1])
0
[/PHP]

---

### Post by jpkotta on 2010-06-11
Numpy must be making a new object every time you access an element of the array.

```

In [14]: id(a[0,1])
Out[14]: 161640272

In [15]: id(a[0,1])
Out[15]: 161097216

In [16]: id(a[0,1])
Out[16]: 162502440

In [17]: type(a[0,1])
Out[17]: <type 'numpy.float64'>

```

---

