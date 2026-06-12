---
title: "c++ #include&lt;new&gt;"
date: 2008-11-03
forum: Programming Talk
---

### Post by guest_user on 2008-11-03
what is this library for?
I don't need to add in #include<new>
to dynamically allocate memory right?
as in
int *pointer = new int;

From here:
[http://www.cplusplus.com/doc/tutorial/dynamic.html](http://www.cplusplus.com/doc/tutorial/dynamic.html)

it says that in new (nothrow) int;, the nothrow object is declared in the new library but when I tried compiling my program without the header file, no errors were given to me by the compiler and everything worked as per normal, so whats the purpose of the new library?

---

### Post by LaRoza on 2008-11-03
The standard libs are often automatically linked.

[http://en.wikipedia.org/wiki/C%2B%2B_standard_library](http://en.wikipedia.org/wiki/C%2B%2B_standard_library)

---

### Post by guest_user on 2008-11-04
but if that is so, why is it that iomanip is not automatically linked when I want to use setprecision() while new library is automatically linked when I want to use new since both belong to the c++ standard library?

---

### Post by LaRoza on 2008-11-04
> **guest_user said:**
> but if that is so, why is it that iomanip is not automatically linked when I want to use setprecision() while new library is automatically linked when I want to use new since both belong to the c++ standard library?

#include has nothing to do with linking, in case my post was confusing. If you don't link iomanip, then it is automatically linked. 

It would depend on the contents of those headers. I have little interest in C++, and haven't touched it recently (my ten foot pole is out for repairs). If the headers' contents were needed, it would matter.

---

