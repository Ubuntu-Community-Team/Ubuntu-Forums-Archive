---
title: "c++ comandline compilers"
date: 2006-03-01
forum: Programming Talk
---

### Post by firefly123 on 2006-03-01
Hi im starting to learn c++ i want to use gEdit, but what comand line compiler shoud i use????? ps im a nubie:)

---

### Post by jerome bettis on 2006-03-01
first you need to install the build-essential package, sudo apt-get install build-essential

g++ hello.cpp to compile it
./a.out  will run it

or

g++ -o hello hello.cpp
./hello

---

### Post by Vanderley Maia on 2006-03-06
Thank's
But I compiled a my program, but I cant execute it :cry: 
How can I do that?

---

### Post by hod139 on 2006-03-06
Depends on how you compiled it.  As jerome bettis wrote, (with some minor modifications by me)

> 
 g++ hello.cpp      **<-- to compile it**
 ./a.out                 **<--  will run it**
 
 or
 
 g++ -o hello hello.cpp  **<-- to compile it**
./hello                          **<--  will run it**


In the first example, the default executable name of a.out was used.  In the second example, jerome bettis specified a name to use (using the -o flag) and changed the execution command to reflect the new name.

---

