---
title: "Multicore programming - what do I use?"
date: 2009-10-19
forum: Programming Talk
---

### Post by helstreak on 2009-10-19
So I have a quadcore and I would really like to use all the cores to run a simulation.  I have experience with parallel programming on a cluster that's already set up with MPI however my computer doesn't have that.  I'm wondering, in order to use all my cores do I need MPI or is there anything else?

Thanks for your help :)

---

### Post by MadCow108 on 2009-10-19
depends on the language
pthreads or openMP for C
boost threads or openMP for C++
openMP is also available for Fortran

openMP is probably the easiest. Especially if all work is done in few loops with little synchronization, a common situation in simulations.

---

### Post by shadylookin on 2009-10-19
If you just make it multithreaded the scheduler should utilize all your cores. On linux with C/c++ you can use the pthread library to do this.

---

### Post by cholericfun on 2009-10-19
openMP is designed for Shared Memory Processors like a quad-core.
MPI is for distributed memory, however you can run MPI on an SMP. as far as i understand, MPI would produce a copy of your program for every core whereas openMP will keep redundant data to a minimum.

heres a little script to run openmp compiled files (from some webpage about openMP) :
```
#!/bin/bash
#usage:    trun [myexe] [threads]
set -u
MYEXE=$1
export OMP_NUM_THREADS=$2
echo "Running $MYEXE on node 'hostname' \
				with $2 threads"
$MYEXE
exit
```

get a few examples to look at and you'll be fine, openmp is not that bad to learn.

---

