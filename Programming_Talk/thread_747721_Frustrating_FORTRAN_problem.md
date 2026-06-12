---
title: "Frustrating FORTRAN problem"
date: 2008-04-06
forum: Programming Talk
---

### Post by nspattak on 2008-04-06
Hi!

I have a strange problem and I am completely unable to think of any possible solution, so please any ideas are more than welcome!

I have a fortran scientific code. This code depends on 2 parameters, nx and ny. This code also uses openmp. The thing is that when I compile with nx,ny>200 with openmp enabled (gcc or ifort) it doesnot run and I get SIGSERV .

pattakosn@stamoz-rulez:~/2dim-P2$ ./my_solver <INPUT
Segmentation fault (core dumped)

 I used gdb and I found out that it is unable to open a file that is later used for writing.

Program received signal SIGSEGV
main$main3_$BLK () at main3.f:54
54            open(8,file='interpolation.m', status='new', access='sequential')

 Can any one please give me any idea? I have no clue as to what is going on. I am using ubunty gutsy and gcc-4.3.0(locally compiled)  or intel 10.1.012

---

### Post by jdrodrig on 2008-04-23
First thought, could it be lack of physical or virtual memory?

Any idea of the memory requirement of puting >200 for your variables?

---

