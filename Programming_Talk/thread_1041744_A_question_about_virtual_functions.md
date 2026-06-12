---
title: "A question about virtual functions"
date: 2009-01-16
forum: Programming Talk
---

### Post by TheMyself on 2009-01-16
There is something that I don't understand about virtual functions. Imagine you have a base class which has 100 derived classes which inherit a  virtual function from the base. You write a program that uses the base class and some of the derived ones. All books say "the compiler builds an array of pointers to the virtual functions in base classes". But does the compiler include all the 100 virtual functions in your binary? I can't get this from the books.

I think it is possible for the complier to find out which virtual class functions are actually used because C++ does not allow dynamic data type change (as far as I know). But do compilers really do that?

---

### Post by snova on 2009-01-16
[QUOTE=TheMyself]I think it is possible for the complier to find out which virtual class functions are actually used because C++ does not allow dynamic data type change (as far as I know). But do compilers really do that?[/QUOTE]

I doubt it. If all your code is separated across files, how is the compiler supposed to know? It never sees all your code at one time.

Also, it is possible to get a pointer to a class from a dynamically loaded library with yet another virtual table in it, and be able to call methods in it without knowing ahead of time what they are (think plugins). If the compiler optimized some of those vtable entries away, it wouldn't work!

So, I'd say probably not...

---

### Post by stroyan on 2009-01-17
The array of pointers to virtual functions is not indexed by the subclasses.
It is indexed by different virtual functions of the base class.
If a base class has virtual functions A, B, and C, then the vtable array will be only three elements long.
The pointer values in the array elements are what changes for different subclasses.
A call to virtual function B will look in the matching pointer array element to find the function that should be called for B from a particular instance of the class.
Instances of different subclasses will use different arrays of pointers.

---

