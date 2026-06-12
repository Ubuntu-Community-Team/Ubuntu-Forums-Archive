---
title: "python ctypes and memory leaks"
date: 2010-09-15
forum: Programming Talk
---

### Post by frikker on 2010-09-15
Hey everyone.  I have a question regarding memory leaks using python's ctypes interface to a shared library.

Let us say I have a small function, like this in lib.c.  It simply takes an array, multiples each value times 3, and modifies an array (returnArray) by setting the values.  This is specifically so that I don't have to call malloc() in my mylib.c file.
```

#include "mylib.h"
// take every element in data, raise to third power, and store in returnArray
// data and returnArray are both length <n>
int triple(double *data, int n, double *returnArray)
{
  int i=0;
 
  for (i=0; i<n; i++)
  {
    returnArray[i] = data[i]*data[i]*data[i];
  }
  return 1;
}

```and mylib.h of course:
```

int triple (double *, int, double *);

```OK.  Now if I were to use this function from a C program, I could do this:
main.c:
```

#include "stdlib.h"
#include "stdio.h"
#include "mylib.h"

int main()
{

    int m = 5;
    double *retValue = (double *)malloc(sizeof(double[m]));
    double array[5] = {1,2,3,4,5};

    int ret = triple(array, m, retValue);
    int i;
    for (i=0; i<m; i++)
    {
       printf("%d) %.3f ", i, retValue[i]);
    }
    printf("\n");
    free (retValue);
    return 0;

}


```quick Makefile:
```

CC=gcc
CCFLAGS=-Wall -fPIC -shared -lm -I. #-02

all:    mylib.so main

mylib.so:    mylib.c mylib.h
        $(CC) $(CCFLAGS) mylib.c -o mylib.so
main:       mylib.c mylib.h main.c
        $(CC) -I. -Wall mylib.c main.c -o main

```I compile and run this (typing 'make' creates both main and mylib.so) and it is just dandy (./main).  malloc() and free() are taken care of, valgrind is happy, and my triple function executes nicely.

But now I move to ctypes where I want to call mylib.triple() from python.  Here we go!

and my python ctypes wrapper (main.py)
```

from ctypes import *
import os
class wrapper(object):
    def __init__(self):
        #path = os.path.split(__file__)[0]
        path = "."
        self.so = CDLL('%s/mylib.so' % path)
    def triple(self, array):
        N = len(array)
        dblArray = c_double*N
        self.so.triple.argtypes=[dblArray,c_int, dblArray]
        outarray = dblArray(*([0]*N))
        inarray = dblArray(*array)
       
        result = self.so.triple(inarray, N, outarray)
        if result == 1:
            return tuple(outarray)
        else:
            return tuple([0]*N)

a = wrapper()
result = a.triple([1,2,3,4,5])
for i in xrange(len(result)):
    print "%d) %.3f" % (i, result[i]),
print ''

``````

Output:
148$ python main.py && ./main
0) 1.000 1) 8.000 2) 27.000 3) 64.000 4) 125.000 
0) 1.000 1) 8.000 2) 27.000 3) 64.000 4) 125.000 

```OK.  Now that is all out there...

[LIST=1]
[*]Does python handle the garbage collection of <inarray> and <outarray> in the python wrapper class automatically? Or do I have to free them before leaving the wrapper.triple function? Obviously there is no explicit call of <malloc> in my python file so I'm not sure what to do.
[*]I feel like I'm spending a lot of time making and copying data types.  Any other suggestions?
[*]Any comments / questions about using ctypes in this way?
[/LIST]
Thanks!!
Blaine

---

### Post by worseisworser on 2010-09-15
See [http://stackoverflow.com/questions/1453776/ctypes-memory-management-how-and-when-free-the-allocated-resources](http://stackoverflow.com/questions/1453776/ctypes-memory-management-how-and-when-free-the-allocated-resources)

---

### Post by nvteighen on 2010-09-16
1. There should be absolutely no problem there. inarray and outarray are Python structures, so Python deals with them, not the shared library.

2. Uh, well, ctypes is like that. You could, for example, set self.so.triple.restype to the required return type and avoid some casting. Also, setting the argtypes makes Python cast whatever you pass to the type desired.

But yes ctypes is verbose and unpractical for big APIs. What some people do is to use SWIG, which generates a Python interface from C (and C++) automatically and *really* nicely (well, it isn't just for Python... check it out!). It's in the repos, install the swig package... ([http://swig.org/](http://swig.org/) for documentation... but it's stupidly easy to use).

3. You've done it really well... and properly wrapped into a class, something I myself always forget to do and well... uh... it turns everything into a mess... :P

---

### Post by frikker on 2010-09-20
> **worseisworser said:**
> See [http://stackoverflow.com/questions/1453776/ctypes-memory-management-how-and-when-free-the-allocated-resources](http://stackoverflow.com/questions/1453776/ctypes-memory-management-how-and-when-free-the-allocated-resources)

Thanks! That was a great read.

> **nvteighen said:**
> 1. There should be absolutely no problem there. inarray and outarray are Python structures, so Python deals with them, not the shared library.

2. Uh, well, ctypes is like that. You could, for example, set self.so.triple.restype to the required return type and avoid some casting. Also, setting the argtypes makes Python cast whatever you pass to the type desired.

But yes ctypes is verbose and unpractical for big APIs. What some people do is to use SWIG, which generates a Python interface from C (and C++) automatically and *really* nicely (well, it isn't just for Python... check it out!). It's in the repos, install the swig package... ([http://swig.org/](http://swig.org/) for documentation... but it's stupidly easy to use).

3. You've done it really well... and properly wrapped into a class, something I myself always forget to do and well... uh... it turns everything into a mess... :P
Thanks as well! You've really just reaffirmed what I thought.  Thanks again!

---

### Post by frikker on 2010-09-20
Also, for any lurkers, inquire within about how to do similar stuff with C++ classes.

---

