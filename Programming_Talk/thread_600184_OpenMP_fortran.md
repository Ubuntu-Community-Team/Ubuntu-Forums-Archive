---
title: "OpenMP fortran"
date: 2007-11-02
forum: Programming Talk
---

### Post by jdrodrig on 2007-11-02
Hi,

I am getting frustrated here...I thought I knew how to do this..

I am on a Dell 620, Core 2 Duo, trying to run some simple fortran programs on SunStudio 12

I compile with the -openmp flag...but when I execute, only one core is being used.....

I changed .bashrc to include: 
PARALLEL=2
OMP_NUM_THREADS=2

am I missing something?

thanks,
D.

---

### Post by LaRoza on 2007-11-02
The program is not using both cores? Or one core is not being used at all by the system.

Not every program will use both cores, especially simple ones.

---

### Post by jdrodrig on 2007-11-02
Thanks LaRoza...

I feel bad now..it seems I forgot the "export PARALLEL" and "export OMP_NUM_THREADS" in the .bashrc...

it is now using both cores...

Thanks!

---

