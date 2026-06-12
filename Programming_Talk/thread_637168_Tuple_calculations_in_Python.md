---
title: "Tuple calculations in Python"
date: 2007-12-10
forum: Programming Talk
---

### Post by b1g4L on 2007-12-10
Is there a Python library / function for performing tuple calculations? For instance, I am storing x,y coordinates like...```
position = (10,20)
```

I want to perform tuple addition, so ```
position = position + 2
``` assigns position to (12,22).

Currently I have written a function to perform tuple addition, but I would like to eliminate it, if there is a more elegant way of doing this. Any help would be appreciated.

---

### Post by Wybiral on 2007-12-10
It sounds like you want to create your own class and overload the addition operator, here's an example:

```
class vec2:

    def __init__(self, x, y):
        self.v = (x, y)

    def __add__(self, b):
        try:
            return vec2(self.v[0] + b, self.v[1] + b)
        except:
            return vec2(self.v[0] + b.v[0], self.v[1] + b.v[1])

    def __str__(self):
        return "vec2(%f, %f)" % (self.v[0], self.v[1])

a = vec2(10, 20)
b = vec2(30, 40)
print a + b
print a + 2

```

I should also note that NumPy has all kinds of operations like this!

EDIT:

To save you a Google, [http://numpy.scipy.org/](http://numpy.scipy.org/)

---

### Post by ghostdog74 on 2007-12-10
```

>>> position = (10,20)
>>> [i+2 for i in position]
[12, 22]
>>> tuple([i+2 for i in position])
(12, 22)


```

---

### Post by b1g4L on 2007-12-10
Thanks for the suggestions. I figured Numeric / NumPy had operations like this, but I've never had a reason to use them. Maybe this is my chance... I also wanted to note that I need the ability to add a tuple to another tuple, not just add a tuple with a constant.

Creating a new class and overloading the + operator is an elegant way to achieve what I want. However, it's not much different than the functions I wrote. The tuples still have to be indexed and added separately. I wonder if it is more or less efficient than functions in Numeric?

---

### Post by pmasiar on 2007-12-10
my bet would be on numpy being more efficient and less buggy than any custom code you could whip in afternoon. And in rare case you will find a bug, fixing it in numpy will fix it for anyone coming to numpy after you.

---

### Post by engla on 2007-12-10
Numpy is more efficient probably; it uses arrays instead of lists and tuples, so it uses much less storage etc. And it's not written in python, much of it is written in C

That said, I couldn't resist.. your new class should be a subclass of tuple of course...
```
class vec (tuple):
    def _binaryop(self, other, op):
        try:
            return vec(op(a,b) for a,b in zip(self, other))
        except:
            raise NotImplementedError
    def __add__(self, other):
        return self._binaryop(other, lambda a,b: a + b)
    def __sub__(self, other):
        return self._binaryop(other, lambda a,b: a - b)
        

r = vec((2,3,4))
t = vec((1,3,4))

print r + t, r-t
```

---

### Post by b1g4L on 2007-12-10
Thanks for your example engla. I ran a quick test to compare the speed of using my function vs. overloading the operators.  I just wanted a rough estimate, and the results showed that using my function is plenty fast for my application. Thanks everyone for your help.

---

