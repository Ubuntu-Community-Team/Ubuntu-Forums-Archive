---
title: "Python ctypes and errcheck"
date: 2009-02-05
forum: Programming Talk
---

### Post by jpkotta on 2009-02-05
I'm using ctypes to access a DLL on Windows (seems to be exactly the same on Linux) from Python.  All of the functions have the same return type (an error code).  I would like to run a python function after every foreign function call that checks for an error and gives a helpful message if there is one.  It seems like errcheck() from ctypes is the correct way to do this, but as far as I can see, I have to set it for each function.  
```
import ctypes
def chk(ret, func, args):
    if ret < 0:
        raise RuntimeError("helpful message")
    return ret

foo = ctypes.windll.foolib
foo.do_this.errcheck = chk
foo.do_that.errcheck = chk
...
```

This is not ideal; like I said before, all the functions return the same type, and there are hundreds of them.  Any suggestions?

---

### Post by imdano on 2009-02-06
Maybe by subclassing ctypes.LibraryLoader and overriding the LoadLibrary method?  You could call the real LoadLibrary method, get the return value, assign the errcheck attribute to your chk function, and then return that.

---

### Post by jpkotta on 2009-02-09
> **imdano said:**
> Maybe by subclassing ctypes.LibraryLoader and overriding the LoadLibrary method?  You could call the real LoadLibrary method, get the return value, assign the errcheck attribute to your chk function, and then return that.

I should say I'm not very familiar with Python.  I'm probably doing something glaringly wrong here.

The errcheck member resides in the _FuncPtr class, which appears to be the class that foreign function pointers belong to.  

(I figured I should do this in Linux since this is a Linux forum.  I think my problem is OS-agnostic.)  If I derive a class from CDLL and have a derived _FuncPtr in that, it doesn't work.  

```

from ctypes import *

def myerrcheck(ret, func, args):
    print "%s returned %d" % (func.__name__, ret)
    return ret

class myCDLL(CDLL):
    class _FuncPtr(CDLL._FuncPtr):
        _flags_ = CDLL._FuncPtr._flags_
        def errcheck(self, ret, func, args):
            return myerrcheck(ret, func, args)

mylibc = myCDLL("libc.so.6")
mylibc.printf("one\n")

mylibc.printf.errcheck = myerrcheck
mylibc.printf("two\n")

libc = CDLL("libc.so.6")
libc.printf.errcheck = myerrcheck
libc.printf("three\n")

```
```

$ python ctype_errcheck.py 
one
two
three
printf returned 6

```
My class doesn't work at all.  What am I doing wrong?

---

### Post by imdano on 2009-02-09
Sorry, I misunderstood exactly what you had to do initially.  What you want to do is override CDLL's __getattr__() method (which will return a _FuncPtr object), so that it first calls the normal CDLL.__getattr__(), gives its return value an errcheck attribute, and then returns that.  I tried implementing it myself and I think it worked.  Here's most of the code: [php]#!/usr/bin/python

from ctypes import *

def myerrcheck(ret, func, args):
    print "%s returned %d" % (func.__name__, ret)
    return ret

class myCDLL(CDLL):
    // Override __getattr__() in here...

mylibc = myCDLL("libc.so.6")
mylibc.printf("one\n")
mylibc.printf("two\n")
mylibc.printf("three\n")
[/php]The output was ```
dan@ubuntop:~$ python help.py 
one
printf returned 4
two
printf returned 4
three
printf returned 6

```Does that look like what you'd expect to see?

---

### Post by jpkotta on 2009-12-12
I forgot to follow up on this.  imdano has the correct solution.  

```
class DAQmxDLL(ctypes.WinDLL):
    """Subclass of WinDLL to set a default _FuncPtr.errcheck."""

    def daqmx_errcheck(self, ret, func, args):
        if ret < 0:
            buf = cstr(1024) # alloc a buffer
            err_str = "NIDAQ call %s failed with error %d.\n" \
		      % (func.__name__, ret)

            # simple
            # if "DAQmxGetErrorString" not in func.__name__:
            #     self.DAQmxGetErrorString(ret, ctypes.byref(buf), len(buf)-1)

            # verbose (same as GetErrorString but returns additional info)
            if "DAQmxGetExtendedErrorInfo" not in func.__name__:
                self.DAQmxGetExtendedErrorInfo(ctypes.byref(buf), len(buf)-1)

            raise DAQmxError(err_str + buf.value)
        return ret

    def __getitem__(self, name):
        func = self._FuncPtr((name, self))
        if not isinstance(name, (int, long)):
            func.__name__ = name
        func.errcheck = self.daqmx_errcheck
        return func

```

---

