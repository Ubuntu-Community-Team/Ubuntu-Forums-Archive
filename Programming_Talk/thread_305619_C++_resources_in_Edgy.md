---
title: "C++ resources in Edgy"
date: 2006-11-23
forum: Programming Talk
---

### Post by ravalox on 2006-11-23
Hi, I'm trying to relearn C++ after years of not using it, I'm writing a simple program and I cannot locate the function: ```
strcat_s
``` with my code, it's supposedly part of a now preferred set of string functions, I'm trying to use it with ```
strcpy_s
``` and I can't seem to locate the dependency that will allow the compiler to find it?  KDevelop simply tells me: ```
/home/tate/deadmanshand/src/Card.cpp:57: error: ‘strcpy_s’ was not declared in this scope
```

Any suggestions would be very helpful.

---

### Post by hod139 on 2006-11-27
strcat_s and strcpy_s are Microsoft specific functions to make string handling in C more secure.  They have been proposed to become a standard, but are not yet.  GCC won't implement these functions unless they become part of the standard.

---

