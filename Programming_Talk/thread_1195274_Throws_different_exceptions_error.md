---
title: "Throws different exceptions error"
date: 2009-06-23
forum: Programming Talk
---

### Post by wbest on 2009-06-23
I'm trying to compile some C++ code (I didn't write it, I'm trying to maintain it/port it from Windows to Linux), but when I try to compile it using g++, I keep getting the error (for certain functions and methods, for example the well-known double foobar function):
 
error: declaration of 'double foobar (...)' throws different exceptions
 
 
Why does it do this? It seems to do this only in Linux, as it has worked fine in Windows.

---

### Post by Habbit on 2009-06-23
It means that the definition of your function throws different exceptions than those in the declaration. Look at the "throw (...)" clause in the declaration - it is a promise by your method to throw _only_ those exceptions and no others. The definition must match the declaration or the compiler will choke.

---

