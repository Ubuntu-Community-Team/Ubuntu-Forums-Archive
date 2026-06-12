---
title: "GCC compiler compiling c files but cpp files are not compiled"
date: 2011-07-12
forum: Packaging and Compiling Programs
---

### Post by neo1110 on 2011-07-12
i have a file name first.c and a second one named fisrt1.cpp
now
gcc -o first.c abc

works

but gcc -0 first1.cpp xyz

is not working as its is saying that
stdio.h:no such file or directory

---

### Post by psusi on 2011-07-12
gcc is the C compiler, g++ is for C++.

---

