---
title: "openmpi issue (fortran)"
date: 2012-01-01
forum: Programming Talk
---

### Post by fal-parsi on 2012-01-01
Disclaimer: I have posted this on the German forum ubuntuuusers.de as well. I will inform both forums asap when the problem is solved.

Hi,

I am trying to use openmpi and my programming language is Fortran. It works in principle on my computer for a small example I have programmed. However, when I try to compile my current project, I get the following error message:

> -*- mode: compilation; default-directory: "/home/----/Documents/Codes/stochGrowth_for_parallel/" -*-
Compilation started at Sun Jan  1 21:53:12

mpif90 stochGrowth_par.f90 -o stochS
/tmp/ccUHrEIW.o: In function `MAIN__':
stochGrowth_par.f90:(.text+0x35e): undefined reference to `mpi_ini_'
collect2: ld returned 1 exit status

Compilation exited abnormally with code 1 at Sun Jan  1 21:53:12

Does anyone have any idea how to fix this problem? Sorry, I am pretty inexperienced. Please also let me know whether you need further information.

Thx,
Parsi

---

### Post by fal-parsi on 2012-01-02
I solved it. I mispelled one of the mpi commands.

---

