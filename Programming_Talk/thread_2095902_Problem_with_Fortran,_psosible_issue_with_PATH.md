---
title: "Problem with Fortran, psosible issue with PATH"
date: 2012-12-18
forum: Programming Talk
---

### Post by gusanto on 2012-12-18
Hello there, I hope my message will get read soon and somebody will give me a solution.
I use fortran to do simulation and gfortran is the compiler I use. Recently I migrated from Ubuntu 10.10 to 12.10. After installing gfortran then I tried to compile and run my fortran programs then the problem started. I succsesfully compiled the program but unable to execute it. (I work in a directory in shared partition, not in HOME directory). When I compiled the program and run it within HOME directory, everything worked fine. On my Ubuntu 10.10, I was able to compile and execute fortran program from every where not only within HOME directory.
This is what I do for compiling and executing fortran program:
gfortran hello.f90 -o hello  # to compile it
./hello                      # to execute it

I'm blind about PATH or anything like it (this has to do with it, I suspect) so please give me direction.
Many thanks.

---

### Post by sffvba[e0rt on 2012-12-18
*Thread moved to **Programming Talk**.*


404

---

### Post by Tony Flury on 2012-12-18
What is the actual error you get ?
Is the shared partition an entirely Ubuntu partition, or is it for instance a shared Samba drive ?

---

