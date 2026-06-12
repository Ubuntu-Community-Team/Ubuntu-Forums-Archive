---
title: "C++ types in GCC"
date: 2010-06-07
forum: Programming Talk
---

### Post by devesa on 2010-06-07
Hello,

I am trying to compile in Ubuntu a C++ program which was previously running in Windows.
I get this problems with some data types and constant that GCC does not recognize:

- HANDLE (type)
- INFINITE (constant)
- LPVOID (type)

Is there any library or equivalent type in GCC?

Thanks a lot!

---

### Post by MadCow108 on 2010-06-07
you can look them up here:
[http://msdn.microsoft.com/en-us/library/aa383751(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa383751(VS.85).aspx)
and provide the typedefs yourself

infinite is provided by math.h but is called INFINITY
you redefine it if necessary:
#include <cmath>
#ifndef INFINITE
#define INFINITE INFINITY
#endif

---

### Post by Milliways on 2010-06-07
> **devesa said:**
> Hello,

I am trying to compile in Ubuntu a C++ program which was previously running in Windows.
I get this problems with some data types and constant that GCC does not recognize:

- HANDLE (type)
- INFINITE (constant)
- LPVOID (type)

Is there any library or equivalent type in GCC?

Thanks a lot!

You will need to make some logic changes, due to the differences between Microsoft API and linux.
In particular HANDLE (Handle to an object) is returned by a number of quite different API which have no direct equivalent. The most common usage is "handle to file", which is handled differently.

---

