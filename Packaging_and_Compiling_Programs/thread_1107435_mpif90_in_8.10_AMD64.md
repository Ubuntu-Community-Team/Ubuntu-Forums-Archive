---
title: "mpif90 in 8.10 AMD64"
date: 2009-03-26
forum: Packaging and Compiling Programs
---

### Post by AlexVader on 2009-03-26
Hi forum,

I have this app, that calls for mpif90 when i make, 

root@iskandhar:/usr/local/flash# make
cd object; make
make[1]: Entering directory `/usr/local/flash/object'
mpif90 -c -fast -r8 -i4   -DN_DIM=2 -DMAXBLOCKS=1000 -DNXB=8 -DNYB=8 -DNZB=1  CosmologicalFunctions.F90
make[1]: mpif90: Command not found
make[1]: *** [CosmologicalFunctions.o] Error 127
make[1]: Leaving directory `/usr/local/flash/object'
make: *** [default] Error 2
root@iskandhar:/usr/local/flash# 

when i type mpif90 in shell, it says that 

root@iskandhar:/usr/local/flash/object# mpif90
The program 'mpif90' can be found in the following packages:
 * libmpich1.0-dev
 * libopenmpi-dev
 * libmpich-mpd1.0-dev
 * libmpich-shmem1.0-dev
Try: apt-get install <selected package>
-bash: mpif90: command not found
root@iskandhar:/usr/local/flash/object# 

but even when i apt-get install each one of those packages i still do not have mpif90 in the system...

How can i build mpif90 in my system...?  will I have to change each occurence of mpif90 in my makefiles to f95 ( I do not run my code with message parsing ) and pray...?  :-)

Thanks in advance

Alex

---

