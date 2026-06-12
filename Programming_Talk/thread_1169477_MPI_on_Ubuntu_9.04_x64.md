---
title: "MPI on Ubuntu 9.04 x64"
date: 2009-05-25
forum: Programming Talk
---

### Post by sreym on 2009-05-25
Good time. I have a task to deal with MPI. I installed *64-bit Ubuntu 9.04* and installed some packackes from standart repo (*lam-runtime, mpich-bin, mpi-doc, libmpich1.0-dev, liblam4, libmpich1.0gf*). I had no purpose to build a cluster, but simply had to write and debug a program for an existing cluster.  
I tried write simple program on C with name **test**:
[php]
#include <stdio.h>
#include "mpi.h"
main(int argc, char **argv) {
  int    numtasks, taskid;
  MPI_Init(&argc, &argv);
  MPI_Comm_rank(MPI_COMM_WORLD, &taskid);
  MPI_Comm_size(MPI_COMM_WORLD, &numtasks);
  printf("%d\n", taskid);
  MPI_Finalize();
}
[/php]I compiled this: 
**#mpicc test.c -o ./test**
Test to run it: 
**#mpiexec -np 2 ./test**
And got an error:
> 
Lamnodes Failed!
Check if you had booted lam before calling mpiexec else use -machinefile to pass host file to mpiexec
I had run lamboot and again run **test**: 
**#lamboot**
**#mpiexec -np 2 ./test**
Now I got this output:
> 
0
0
-----------------------------------------------------------------------------
It seems that [at least] one of the processes that was started with
mpirun did not invoke MPI_INIT before quitting (it is possible that
more than one process did not invoke MPI_INIT -- mpirun was only
notified of the first one, which was on node n0).

mpirun can *only* be used with MPI programs (i.e., programs that
invoke MPI_INIT and MPI_FINALIZE).  You can use the "lamexec" program
to run non-MPI programs over the lambooted nodes.
-----------------------------------------------------------------------------
mpirun failed with exit status 252
I think that 2 processes wrote own **taskid** that was 0 both. And next you see error of did not invoke of  MPI_INIT and MPI_FINALIZE. In addition **mpiexec**, I also tried to use **mpirun**. Result was the same. I tried **lamexec**, I didn't got any errors but **taskid** also was 0.
P.S. I am grateful for the assistance or at least for the fact that you have read this long post. And sorry for my english.

---

### Post by Sunnz on 2009-05-25
This probably doesn't help as I can't reproduce the error here... but I am using openmpi instead and your code runs fine here, for -np 2 it prints

0
1

So it could be just lam but I haven't used it so I really don't know... at least we'll know your code work on openmpi though.

---

