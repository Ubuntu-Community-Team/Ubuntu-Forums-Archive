---
title: "Python - numpy array slicing"
date: 2010-06-27
forum: Programming Talk
---

### Post by eckeroo on 2010-06-27
I'm struggling to create a single column array from an already existing array.

A=array([[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]])

Using numpy, how do I create a column array from A? 

So that

B = ([[1],[5],[9],[13]])

Using B=A[:,0] and then B.transpose() doesn't work as it returns a flat array.

---

### Post by eckeroo on 2010-06-27
I've found one way of doing it:

B=A[:,0]

then

B.reshape(size(B),1)

which returns:

array([[ 1],
       [ 5],
       [ 9],
       [16]])

But why can't B.transpose() do the same??

---

### Post by Gruu on 2010-07-02
In Python, one-dimensional vectors don't have any notion of "column" or "row" to them; a 1-d vector is just a vector. If you *really* want to make it a "column vector", you can use newaxis (part of numpy), which is a little more notationally convenient than reshape:
```

B = A[:,0]
B = B[:,newaxis]

```
The .transpose() function simply reverses the order of the dimensions (see B.shape). If there's only one dimension, then reversing gives you the exact same thing.

You might also look into the matrix class, although this is usually not recommended:
[http://docs.scipy.org/doc/numpy/reference/generated/numpy.matrix.html](http://docs.scipy.org/doc/numpy/reference/generated/numpy.matrix.html)

Also, a programming-oriented question like this might get a bit more response at a place like stack overflow ([www.stackoverflow.com](www.stackoverflow.com)) or the numpy mailing list ([http://www.scipy.org/Mailing_Lists](http://www.scipy.org/Mailing_Lists)).

Hope that helps!

---

