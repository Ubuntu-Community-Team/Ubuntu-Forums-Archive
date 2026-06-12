---
title: "float.h - where to find missing C libraries?"
date: 2010-08-03
forum: Programming Talk
---

### Post by ozmotion on 2010-08-03
I'm just starting out with learning c++ in the ubuntu environment.

I've been poking around the C/C++ library headers as they've come up in my learning, and I've been able to find them all so far in /usr/include (for C) and /usr/include/c++.

I wanted to look at the contents of the float.h file. Specifically, to get a listing similar to **limits.h** that tells me number of bits used for the mantissa, exponent, etc. I noticed that there's a **cfloat** file in the c++ directory, but it's a forwarding header that just points to **float.h**. I can't find this **float.h** anywhere, though. Any ideas please?

(im running 10.04 with pretty much everything standard.)

---

### Post by Bachstelze on 2010-08-03
It should be in /usr/lib/gcc/<platform>/<version>/include.  It won't tell you much, though. :p  This is really something you should know by heart.

---

### Post by ozmotion on 2010-08-03
> **Bachstelze said:**
> It should be in /usr/lib/gcc/<platform>/<version>/include.  It won't tell you much, though. :p  This is really something you should know by heart.

thanks, that worked. and you were also right on the point you made. 

The header defines stuff like 'FLT_MAX' as '__FLT_MAX__'. Where is the preprocessor grabbing values like "__FLT_MAX__" from? 

anyway im marking this thread as solved, but if you have time to continue the discussion a bit thats cool too

edit: oops, looks like i dont have permission to mark 'solved'

---

### Post by Bachstelze on 2010-08-03
> **ozmotion said:**
> 
The header defines stuff like 'FLT_MAX' as '__FLT_MAX__'. Where is the preprocessor grabbing values like "__FLT_MAX__" from? 


Actually I have /usr/include/float.h here on OS X:

```
firas@tsukino ~ % grep MAX /usr/include/float.h 
#ifndef __FLT_MAX__
#define __FLT_MAX__ 3.40282347e+38F
#ifndef __FLT_MAX_EXP__
#define __FLT_MAX_EXP__ 128
#ifndef __FLT_MAX_10_EXP__
#define __FLT_MAX_10_EXP__ 38
#ifndef __DBL_MAX__
#define __DBL_MAX__ 1.7976931348623157e+308
#ifndef __DBL_MAX_EXP__
#define __DBL_MAX_EXP__ 1024
#ifndef __DBL_MAX_10_EXP__
#define __DBL_MAX_10_EXP__ 308
#ifndef __LDBL_MAX__
#define __LDBL_MAX__ 1.7976931348623157e+308
#ifndef __LDBL_MAX_EXP__
#define __LDBL_MAX_EXP__ 1024
#ifndef __LDBL_MAX_10_EXP__
#define __LDBL_MAX_10_EXP__ 308
#undef FLT_MAX_EXP
#undef DBL_MAX_EXP
#undef LDBL_MAX_EXP
#define FLT_MAX_EXP	__FLT_MAX_EXP__
#define DBL_MAX_EXP	__DBL_MAX_EXP__
#define LDBL_MAX_EXP	__LDBL_MAX_EXP__
#undef FLT_MAX_10_EXP
#undef DBL_MAX_10_EXP
#undef LDBL_MAX_10_EXP
#define FLT_MAX_10_EXP	__FLT_MAX_10_EXP__
#define DBL_MAX_10_EXP	__DBL_MAX_10_EXP__
#define LDBL_MAX_10_EXP	__LDBL_MAX_10_EXP__
#undef FLT_MAX
#undef DBL_MAX
#undef LDBL_MAX
#define FLT_MAX		__FLT_MAX__
#define DBL_MAX		__DBL_MAX__
#define LDBL_MAX	__LDBL_MAX__

```

but it's not on Ubuntu.  Perhaps you could try

```
grep -r __FLT_MAX__ /usr
```

---

### Post by Paul820 on 2010-08-04
Look in limits.h for C, or climits for C++

---

