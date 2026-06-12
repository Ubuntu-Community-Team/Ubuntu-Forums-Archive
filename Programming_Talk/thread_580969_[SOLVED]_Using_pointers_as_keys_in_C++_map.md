---
title: "[SOLVED] Using pointers as keys in C++ map"
date: 2007-10-19
forum: Programming Talk
---

### Post by bluedalmatian on 2007-10-19
If I declare a C++ map which uses pointers to an object as keys, 

std::map<MyObject*,int>


when I search for a particular key, am I right in thinking it will match if the pointer points to the same memory address?

Thanks

---

### Post by CptPicard on 2007-10-19
Yep, that's correct... it will match with the same pointer value, that is, the same memory location...

---

### Post by Zdravko on 2007-10-19
Yes, but you would like to define several comparison operators for MyObject*?

---

