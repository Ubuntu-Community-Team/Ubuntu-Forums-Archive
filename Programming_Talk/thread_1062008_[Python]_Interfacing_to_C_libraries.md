---
title: "[Python] Interfacing to C libraries"
date: 2009-02-06
forum: Programming Talk
---

### Post by nvteighen on 2009-02-06
Hi there,
I've been learning how to interface with C libraries from Python. Quite easy, but for some reason, I can't make this work with the C Standard Math Library (libm.so).

Look:
```

ugi@UGI:~$ python
Python 2.5.2 (r252:60911, Jan  4 2009, 17:40:26) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import ctypes
>>> libc = ctypes.CDLL("libc.so.6")
>>> libc.printf("Hello!\n")
Hello!
7
>>> libm = ctypes.CDLL("libm.so")
>>> libm.pow(8, 9)
34
>>> libm.pow(8, 9)
14370
>>> libm.pow(8, 9)
12322
>>> ctypes.c_double(libm.pow(7, 9)).value
99.0
>>> ctypes.c_double(libm.pow(7, 9)).value
14435.0
>>> ctypes.c_double(libm.pow(7, 9)).value
12387.0
>>> 

```

What you see there is how it works for the C Std. Lib (libc): I can use printf() and it even returns the integer 7 (which is usually dismissed in C code). But libm.pow() doesn't work... I first thought it may be because a c_double was needed, but as you see... it also didn't work that way.

Any reason why this is occurring? Am I doing something wrong? Thanks!

---

### Post by WW on 2009-02-06
> **nvteighen said:**
> 
Am I doing something wrong?

A floating point number is not a type that is automatically understood by ctypes, so in this case, you have to tell ctypes what the return value type and argument types are.  Here's an ipython session showing one way to do this:

```

In [1]: import ctypes

In [2]: libm = ctypes.CDLL("libm.so")

In [3]: libm.pow.argtypes = [ctypes.c_double,ctypes.c_double]

In [4]: libm.pow.restype = ctypes.c_double

In [5]: libm.pow(4.0,0.5)
Out[5]: 2.0

In [6]: 

```
Find more info. about ctypes, arguments and returns values [here](http://docs.python.org/library/ctypes.html).

---

### Post by nvteighen on 2009-02-07
Hey, thanks! For some reason I missed that part, as I was using the same doc you gave me.

Now it's clear to me... and wow, it's pretty easy to do this.

---

