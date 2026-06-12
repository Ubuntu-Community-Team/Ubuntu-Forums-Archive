---
title: "Python - arrays and two dimensional arrays"
date: 2006-09-22
forum: Programming Talk
---

### Post by ironfistchamp on 2006-09-22
Hey all

In C++ arrays and multi-dimensional arrays were really easy. I am wondering if it is possible to do the same in python. I want a two dimensional array with the max number of 20 "boxes" but I am unsure of the synatx and the documentation I have found ahs just confused me. What do I need to get the end result as described above?

Thanks for any help

Ironfistchamp

---

### Post by Tomosaur on 2006-09-22
there are various modules which will make maths a bit more advanced in your python programs. Numeric is one such module. However, to declare an array in python:

x = array([1, 12, 80, 5, 3])

You can then use slicing and whatnot to play with them. Python's arrays are a little different than what you're used to, but you should have no trouble doing whatever you need. This page is the python documentation for arrays:

[http://www.pentangle.net/python/handbook/node39.html](http://www.pentangle.net/python/handbook/node39.html)

---

### Post by Arevos on 2006-09-22
A multidimensional array is merely an array of arrays; this is as true in C++ as it is in Python.

```
one_dimensional_list = [1, 2, 3]
two_dimensional_list = [[1, 2], [3, 4]]

one_dimensional_list[1]     # returns 2
two_dimensional_list[1]     # returns [3, 4]
two_dimensional_list[1][0] # returns 3
```

---

### Post by ironfistchamp on 2006-09-22
Excellent thanks for the help. I shall put it to good use.

Thanks again

Ironfistchamp

---

### Post by maubp on 2006-09-22
The "list of lists" trick is good enough for simple usage.

For speed/serious maths, you should look at dedicated the array package NumPy, [http://numpy.scipy.org/](http://numpy.scipy.org/)

Its based on the older Numeric (which is still very much in use) with additions from its cousin Numarray.

Numeric has the advantage of a very easy install using the standard repositories.  On the command line:

apt-get install python-numeric

NumPy doesn't seem to be included, so you'd have to download and install it yourself - its not too tricky ;)

---

### Post by Steveire on 2006-09-22
python-numpy is included, but it's not the latest version. There's work being done to update it. [https://launchpad.net/distros/ubuntu/+source/python-scipy/+bug/57070](https://launchpad.net/distros/ubuntu/+source/python-scipy/+bug/57070)

(scipy depends on numpy)

---

