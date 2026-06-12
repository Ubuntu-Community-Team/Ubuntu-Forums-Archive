---
title: "C / C++ Programming in Ubuntu"
date: 2007-04-23
forum: Programming Talk
---

### Post by akash.yakovsky on 2007-04-23
Can someone give just the compilation and running commands in Ubuntu to compile and run a C / C++ program? Plz give the most general form of them.

--Akash.

---

### Post by Wybiral on 2007-04-23
gcc program.c
g++ program.cpp
./a.out

---

### Post by Wybiral on 2007-04-23
Also...

gcc libcode.c -c -o my_object_file.o
gcc program.c my_object_file.o -o my_program

---

