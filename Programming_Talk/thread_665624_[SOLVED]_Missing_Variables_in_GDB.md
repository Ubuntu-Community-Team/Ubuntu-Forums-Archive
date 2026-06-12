---
title: "[SOLVED] Missing Variables in GDB"
date: 2008-01-12
forum: Programming Talk
---

### Post by The_PhAnT0m on 2008-01-12
I am trying to write a small C++ program that uses plenty of pointers and loops. I have run into a few logical errors and I am trying to use gdb to debug it. For some reason when I step through my program, it skips over the decleration of some of my variables and when I try to print the value of the variable, it says "$1 = <value optimized out>" Anybody know why? I am fairly new to programming in linux and gcc, so please forgive my ignorance.

---

### Post by hod139 on 2008-01-12
Make sure when you compile your code that you enable debugging symbols and disable optimizations.

```

g++ -g -O0

```

The first flag (-g) enables the debugging symbols, and the second flag (-O0) disables optimizations; the flag is 
  -'Oh' 'Zero'

---

### Post by The_PhAnT0m on 2008-01-12
Hey thanks! I had put $(CFLAGS) as an argument in my makefile. I had suspected optimizations had something to do with it but I did not have CFLAGS set in BASH. And then I remembered that I had set CFLAGS=-O3 as an environmental variable in my IDE. LOL! Thanks again!

---

