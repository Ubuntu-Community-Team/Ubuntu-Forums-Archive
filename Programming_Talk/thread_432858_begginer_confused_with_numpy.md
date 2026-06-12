---
title: "begginer confused with numpy"
date: 2007-05-04
forum: Programming Talk
---

### Post by jeremytaylor on 2007-05-04
Hi, I'm a newcomer to python and want to use the numpy package for my work. I think I must still be confused about the differences between the way mutable and immutable objects are passed into functions so maybe someone can help me understand.

As far as I know numpy arrays are mutable. Therefore why, in the following code, does the array a not change its value?

```

from numpy import *

def f(x) :
    
    y = array([[1, 2],[3,4]])
    x = y.copy()

    return None


a = array([[1, 1],[1,1]])
print a
f(a)
print a

```

Any help would be much appreciated.
Jeremy

---

### Post by WW on 2007-05-04
Your array **a** refers to a block of data that holds the elements of the array.  After calling f, **a** still refers to the same block of data; f does not change that.  What happens in f is that initially, **x** refers to the same block of data as **a**, but when you say "x = y.copy()", **x** now refers to a different block of data; you have not changed the original block of data. When f returns, **a** still refers to the original block of data.

If you want the *contents* of **a** to be changed by the function f, don't reassign **x** to a new array; instead, changed the contents of **x**. For example, try this:
```

from numpy import *

def f(x) :

    x[0,0] = 99
    x[1,1] = -1    

    return None


a = array([[1, 1],[1,1]])
print a
f(a)
print a

```

---

### Post by baltimark on 2007-05-04
Does this code clear things up at all? 
```

from numpy import *

def f(x) :    
    y = x.copy()
    y[0][0] = 3

    return None

def g(x):
    y = x
    y[0][0] = 3
    return None

def h(x):
    x[0][0] = 5
    return None

a = array([[1, 1],[1,1]])
print "a = \n" ,a
f(a)
print "after f,  a = \n", a
g(a)
print "after g, a = \n", a
h(a)
print "after h, a = \n", a

```
You're probably trying to investigate the difference between functions f and g. 

So, in 'f', I create a separate copy of x. That SHOULDN'T change 'a' when I change the copy. And it doesn't. 

But, in 'g', the references are assigned. 

In your example, x and a are the same thing when you go into the function, but then you assign x to something new. It doesn't carry 'a' along. That reference is just hanging now, really. It doesn't move the things from y into x's location. It moves x to somewhere else. 

This guy takes a stab at it. . .

[http://www.goldb.org/goldblog/CommentView,guid,4eb92070-c279-44b3-ac2a-5d1c4f3e8115.aspx](http://www.goldb.org/goldblog/CommentView,guid,4eb92070-c279-44b3-ac2a-5d1c4f3e8115.aspx)

On that page, it says this 

*Alex is right that trying to shoehorn Python into a "pass-by-reference" or "pass-by-value" paradigm is misleading and probably not very helpful. In Python every variable assignment (even an assignment of a small integer) is an assignment of a reference. Every function call involves passing the values of those references.*

---

### Post by jeremytaylor on 2007-05-04
Thank you so much both of you! Starting to get the hang of it (too many years programming fortran eek)

Jeremy

---

### Post by dwblas on 2007-05-04
I think this is what you want.  You have to return the updated array, otherwise it remains local to the function and is destroyed when the function exits.
```
from numpy import *

def f(x) :
    
    y = array([[1, 2],[3,4]])
    x = y.copy()

    return x


a = array([[1, 1],[1,1]])
print a
a = f(a)
print a
```

---

