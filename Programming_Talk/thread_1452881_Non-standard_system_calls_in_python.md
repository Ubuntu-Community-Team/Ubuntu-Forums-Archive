---
title: "Non-standard system calls in python"
date: 2010-04-12
forum: Programming Talk
---

### Post by DBQ on 2010-04-12
Hi, is there a way in python to call an os-specific system calls which are not defined in python?

I.e. in C there is a syscall() function which allows you to call any system call given the system call number. Does python have something similar?

I searched all over the place, but was only able to find how to call common system calls such as getpid().

---

### Post by phrostbyte on 2010-04-12
import ctypes

libc = ctypes.CDLL("libc.so.6")
libc.getpid()

:P

---

### Post by DBQ on 2010-05-02
Thank You! This is really helpful!

What if I wanted to call a C function which relies on passing something by reference:

e.g. Suppose I have a python string str = "hello". Can I do the above, and then say libc.memset(str, 'x', len(str))? It seems that I cannot - because after the system call the string is set to some strange character, but not 'x' (I tried it).

Any suggestions?

---

### Post by Tony Flury on 2010-05-02
> **DBQ said:**
> Thank You! This is really helpful!

What if I wanted to call a C function which relies on passing something by reference:

e.g. Suppose I have a python string str = "hello". Can I do the above, and then say libc.memset(str, 'x', len(str))? It seems that I cannot - because after the system call the string is set to some strange character, but not 'x' (I tried it).

Any suggestions?

Why would you want to do that - You are for a start assuming you know how python stores a string, that the value that gets passed to the function  is a valid addrees that can be memset - it might be an address - but it might not be the storage area where the string is stored - it might well be the address of a class structure which defines a lot of attributes which you would stomp over.

If you want to do direct memory access into python data structures then you would need to write a C wrapper function that unpacks the python data structure, and passes something sensible to the system library functions.

---

### Post by nvteighen on 2010-05-02
It's actually really easy. No need to write wrapper functions because ctypes already has them. Read this: [http://docs.python.org/library/ctypes.html](http://docs.python.org/library/ctypes.html)

What you do is to "declare" (as you were in C) the arguments' and return value's data types of the foreign function, using the Python wrappers shown in the link I gave you. That way, Python will know how to deal with it automatically each time you call it.

An example with memset:
```

>>> import ctypes
>>> libc = ctypes.CDLL("libc.so.6")
>>> libc.memset.argtypes = [ctypes.c_void_p, ctypes.c_char, ctypes.c_uint]
>>> libc.memset.restype = ctypes.c_void_p
>>> string = "hello"
>>> libc.memset(string, "x", len(string))
149347988
>>> string
'xxxxx'
>>> 

```

Notice that memset's signature is actually void *memset(void *, **int**, size_t). I forced the second argument to be a character so the ASCII conversion is done automatically; a kind of weird type casting if you may say so. The correct way would have been to set the argument type for memset's wrapper to ctypes.c_int and create a Python function that turns a character into its integer ASCII value.

---

### Post by trent.josephsen on 2010-05-02
> **DBQ said:**
> What if I wanted to call a C function which relies on passing something by reference

Nit: C doesn't have pass-by-reference.  C pointers are first-class objects which are passed into functions in the same way as other objects.  IIRC C++ can use pass-by-reference if you declare your functions in a certain way.

[QUOTE=nvteighen]Notice that memset's signature is actually void *memset(void *, int, size_t). I forced the second argument to be a character so the ASCII conversion is done automatically; a kind of weird type casting if you may say so. The correct way would have been to set the argument type for memset's wrapper to ctypes.c_int and create a Python function that turns a character into its integer ASCII value.[/QUOTE]
You mean like ord('x')? ;)

---

### Post by CptPicard on 2010-05-02
> **trent.josephsen said:**
> C pointers are first-class objects which are passed into functions in the same way as other objects.

More like -- C pointers are primitive value types just like every other type in C (yes, I include structs, arrays), and they get passed by value like everything else.

---

### Post by nvteighen on 2010-05-02
> **trent.josephsen said:**
> 
You mean like ord('x')? ;)

Well, didn't know about that. Correcting my previous example to fully conform to memset's interface:
```

>>> import ctypes
>>> libc = ctypes.CDLL("libc.so.6")
>>> libc.memset.argtypes = [ctypes.c_void_p, ctypes.c_int, ctypes.c_uint]
>>> libc.memset.restype = ctypes.c_void_p
>>> string = "hello"
>>> libc.memset(string, ord('x'), len(string))
167583380
>>> string
'xxxxx'
>>> 

```

---

### Post by DBQ on 2010-05-02
Thank you everyone for your replies -- I will give it a try and will let you know how it went.

Cheers.

---

### Post by wmcbrine on 2010-05-02
BTW, I know it's just an example, but the above code makes Python's immutable strings, mutable. :( If you wanted to do it in a Pythonic way:

```
>>> string = 'hello'
>>> string = 'x' * len(string)
>>> string
'xxxxx'
```

---

### Post by Tony Flury on 2010-05-02
This does not make ths string mutable - it replaces the reference to one sequence of characters with a reference to another sequence.

The Original sequence of characters ("hello") does not change, and remains intact if the string is still referred to.

in python 
```

>>> a = "hello"
>>> b = a
>>> a,b
('hello', 'hello')
>>> a = "x" * len(a)
>>> a,b
('xxxxx', 'hello')

```

---

### Post by trent.josephsen on 2010-05-02
> **CptPicard said:**
> More like -- C pointers are primitive value types just like every other type in C (yes, I include structs, arrays), and they get passed by value like everything else.

I considered phrasing it something like that, but it ignores the detail of "array decay" (the name of an array decays into the address of its first element).  I just tried to avoid that altogether, because there are several different interpretations of that feature depending on when and where you learned C.

Also I hate the term "primitive type". :D

---

### Post by wmcbrine on 2010-05-02
> **Tony Flury said:**
> This does not make ths string mutableYes, that's what I was saying. It's the version that calls libc.memset() that makes it mutable. Which I considered a bad thing... hence my alternative, which works in a normal Python way, with immutable strings. (It's a lot simpler, too.) Just in case anyone actually wanted to use memset() because they thought it was useful/needed for the particular purpose of making a string of x's of a given length, instead of just being an example of calling something from libc.

```
>>> import ctypes
>>> libc = ctypes.CDLL('libc.so.6')
>>> libc.memset.argtypes = [ctypes.c_void_p, ctypes.c_int, ctypes.c_uint]
>>> libc.memset.restype = ctypes.c_void_p
>>> a = 'hello'
>>> b = a
>>> libc.memset(a, ord('x'), len(a))
137233844
>>> a
'xxxxx'
>>> b
'xxxxx'
```

---

### Post by DBQ on 2010-05-27
Sorry to resurrect this thread, but what if I wanted to pass an array of long integers as a parameter to a C function from python, and expect the function to modify an array?  I tried the above approach but it did not work for non-strings.

---

