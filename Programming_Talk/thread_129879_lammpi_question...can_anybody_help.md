---
title: "lam/mpi question...can anybody help?"
date: 2006-02-14
forum: Programming Talk
---

### Post by hyperpsyched on 2006-02-14
Hi... I am running lam on my home machine and cannot test my program because mpi running under lam returns 0 as the rank of all the processes. Dies anybody know if there is way to force lam to give processes differnt ranks when running on a single processor?

A total shot in the dark here...

---

### Post by Zwalther on 2006-02-16
Every process should have another rank no matter what processor they run on. You could start 10 processes on your machine and they all should have a different rank.

How do you start your program? And did you call MPI_Init before MPI_Comm_rank?

---

### Post by hyperpsyched on 2006-02-16
The problem is that I installed both mpich and lam and the lam daemon does not play nice with mpich's mpirun command. Uninstalled mpich and lam and reinstalled lam and bingo. One problem though... I needed to add support for exceptions and this needs to be added at configure time, before compilation and adept does not allow this. I am starting to see the limitations of adept, where someone not so familiar with kde/linux can easily download packages but if an advanced user needs to specially configure that software before compilation they are SOL. Anyway problem solved with lots of help from Jeff at OpenMPI/LamMPI.

---

### Post by Zwalther on 2006-02-17
It is possible to have both versions (mpich and lam) installed. But if you want to use mpich's mpirun, you should also link against the mpich libraries. The same goes for LAM.

Anyway, problem solved, good luck.

---

