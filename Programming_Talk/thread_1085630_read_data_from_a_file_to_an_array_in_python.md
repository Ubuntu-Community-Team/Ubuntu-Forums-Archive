---
title: "read data from a file to an array in python"
date: 2009-03-03
forum: Programming Talk
---

### Post by adamsnative on 2009-03-03
Hi
I am having some numeric values in a file , every row is having the same number of values ie suppose 5 values in each row n 10 rows of data so data is in a 10X5 pattern.
How can i read this data into an array . I am using numpy and sci pi modules with python 2.5.Plz help its urgent n very important

---

### Post by ssam on 2009-03-03
have a look at [http://www.scipy.org/Cookbook/InputOutput](http://www.scipy.org/Cookbook/InputOutput) that has some examples.

---

### Post by adamsnative on 2009-03-05
the link you gave is a very old one and python 2.5 is giving errors with it. So plz help with some other resorces and i will be happy if u can give an example

---

### Post by mnemonik on 2009-03-05
pretty sure you could do something like this (not one hundred percent on my use but I know .readlines() sends it to a list which is the python equivalent of an array afaik, i'm new with this stuff too)
[PHP]
inList = raw_input("Type the filename: ")

in_file = open(inList, "r")
list = in_file.readlines()
in_file.close()
[/PHP]

---

### Post by WW on 2009-03-05
> **adamsnative said:**
> the link you gave is a very old one and python 2.5 is giving errors with it. So plz help with some other resorces and i will be happy if u can give an example
What errors do you get?  [loadtxt()](http://www.scipy.org/Numpy_Example_List_With_Doc#head-88ade192dacf0c15e4f1377096134ee559df07a0) works for me:
```

$ cat data.txt
 1.0   2.0   3.0
 4.0   5.0   6.0
 7.0   8.0   9.0
10.0  11.0  12.0
13.0  14.0  15.0
$ cat data.csv
1.0, 2.0, 3.0
4.0, 5.0, 6.0
7.0, 8.0, 9.0
10.0, 11.0, 12.0
13.0, 14.0, 15.0
$ python
EPD Py25 (4.1.30101) -- http://www.enthought.com/epd

Python 2.5.2 |EPD Py25 4.1.30101| (r252:60911, Dec 19 2008, 15:28:32) 
[GCC 4.0.1 (Apple Computer, Inc. build 5370)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
>>> a = numpy.loadtxt('data.txt')
>>> a
array([[  1.,   2.,   3.],
       [  4.,   5.,   6.],
       [  7.,   8.,   9.],
       [ 10.,  11.,  12.],
       [ 13.,  14.,  15.]])
>>> b = numpy.loadtxt('data.csv',delimiter=',')
>>> b
array([[  1.,   2.,   3.],
       [  4.,   5.,   6.],
       [  7.,   8.,   9.],
       [ 10.,  11.,  12.],
       [ 13.,  14.,  15.]])
>>> 

```

---

### Post by Martin Witte on 2009-03-05
or in just plain python
```

martin@toshibap200:~$ cat data.txt
 1.0   2.0   3.0
 4.0   5.0   6.0
 7.0   8.0   9.0
10.0  11.0  12.0
13.0  14.0  15.0

```

```

martin@toshibap200:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> f = open('data.txt')
>>> d = f.readlines()
>>> print [x.split() for x in d]
[['1.0', '2.0', '3.0'], ['4.0', '5.0', '6.0'], ['7.0', '8.0', '9.0'], ['10.0', '11.0', '12.0'], ['13.0', '14.0', '15.0'], []]
>>> f.close()
>>> 

```

---

