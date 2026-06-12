---
title: "compileing prob"
date: 2011-01-23
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2011-01-23
cpan/ExtUtils-CBuilder/t/03-cplusplus..........................cc: error trying to exec 'cc1plus': execvp: No such file or directory cc: error trying to exec 'cc1plus': execvp: No such file or directory


What does this mean and how do i fix it i do have gcc installed when i get this error.

---

### Post by SevenMachines on 2011-01-24
Try installing build essential

$ sudo apt-get install build-essential

---

### Post by SevenMachines on 2011-01-24
Ah, forum flakiness :*) 
Anyways..

It's g++ and not gcc its looking for there

cc1 = gcc or other c compiler
cc1plus = g++ or other c++ compiler

see 
$ apt-file search cc1plus

---

### Post by pythonsyntax on 2011-01-24
thank it works:)

---

