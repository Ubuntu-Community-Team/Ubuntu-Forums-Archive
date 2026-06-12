---
title: "Problem loading IPP shared libraries"
date: 2010-10-15
forum: Programming Talk
---

### Post by kayss on 2010-10-15
Hello everyone,

I am programming in ubuntu linux 9.10.

I have a runtime error when my application try to acces to share library libippcore.so.6.1.

However this library is in /opt/intel/ipp/6.1.1.042/ia32/sharelib/libippcore.so.6.1

And my IPPROOT variable is: /opt/intel/ipp/6.1.1.042/ia32/

I don't knok what is the problem.


Please, someone can help me...
Thank you

---

### Post by spjackson on 2010-10-15
> **kayss said:**
> 
I have a runtime error when my application try to acces to share library libippcore.so.6.1.

What is the runtime error? How are you running your application, directly or via a script? Is your application linked to that library or are you trying to load it with dlopen()?
> 
However this library is in /opt/intel/ipp/6.1.1.042/ia32/sharelib/libippcore.so.6.1

And my IPPROOT variable is: /opt/intel/ipp/6.1.1.042/ia32/
The problem could be that you need to set the LD_LIBRARY_PATH environment variable, but it depends on what your error is really.

---

