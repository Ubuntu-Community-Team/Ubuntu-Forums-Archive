---
title: "Problem with compiling C++"
date: 2011-03-12
forum: Programming Talk
---

### Post by 23Andrew on 2011-03-12
I ran across a problem while running:
```
gcc Core.cpp -o debug.out
```
It came up with:
```
/tmp/ccCpxpcr.o: In function `__static_initialization_and_destruction_0(int, int)':
Core.cpp:(.text+0x27): undefined reference to `std::ios_base::Init::Init()'
Core.cpp:(.text+0x2c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccCpxpcr.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```
But when I used:
```
c++ Core.cpp -o debug.out
```
It compiled fine. Can anyone shed any light on this situation?

---

### Post by gmargo on 2011-03-12
**gcc** is a C compiler.  [B]
c++[/B] is a C++ compiler.

If you are compiling C++, use **c++** (or **g++**).

---

### Post by Shpongle on 2011-03-12
Gcc is a c compiler , while g++ , c++ are c++ compilers.
Edit: late to the party

---

### Post by 23Andrew on 2011-03-12
I feel stupid now. :p

Thanks guys.

---

### Post by Shpongle on 2011-03-12
Don't feel stupid, we never stop learning during our lifetime

---

