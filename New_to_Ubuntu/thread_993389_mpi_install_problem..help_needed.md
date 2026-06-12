---
title: "mpi install problem..help needed"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by danijela on 2008-11-25
Hi,
I want to install MPICH2 (on ubuntu)

After this command:
cd /home/ Desktop/ mpich2-1.0/ configure \
 -prefix=/home/ Desktop/mpich2-install 2>&1 | tee configure.log

I have problems with next command
make 2>&1 tee make.log

Error: No rule to make target `tee'.  Stop.

*sudo* doesn't help here, cuz also when I try
just *make* it says :  No targets specified and no makefile found.  Stop.

:confused:

---

### Post by amauk on 2008-11-25
where are you getting these commands from?
some tutorial somewhere?

---

### Post by danijela on 2008-12-09
> **amauk said:**
> where are you getting these commands from?
some tutorial somewhere?

yes tutorial

---

### Post by karlr42 on 2008-12-09
```
sudo apt-get install mpich-bin
```
Wouldn't that work for you?
EDIT: changed the command

---

### Post by danijela on 2008-12-11
> **karlr42 said:**
> ```
sudo apt-get install mpich
```
Wouldn't that work for you?

eh no,i tried... :(
ill figure something out anyway..tnx

---

### Post by karlr42 on 2008-12-11
What didn't work about it? It would be much easier than compiling from source. 
EDIT: I got the command wrong, try it now and see what happens

---

### Post by chianchiere on 2009-02-06
If you want to use MPICH to compile programs you should also install development libraries:

```
sudo apt-get install mpich-bin libmpich1.0-dev mpi-doc
```

there is also the option of installing OpenMPI 

```
sudo apt-get install openmpi-bin openmpi-doc libopenmpi-dev
```

If you want to execute the code you have compiled on your Ubuntu machine, there is anyhow a problem: mpi programs need a lamboot enviroment to be executed, buth both mpich and openmpi won't run under the lamboot enviroment you can get via Ubuntu repositories.

So the final solution to compile/run MPI programs is to install a complete LAM enviroment:

```
sudo apt-get install  lam-runtime lam4-dev lam-mpidoc
```

If you need BOTH lam and mpich (for example to compile [[COLOR="RoyalBlue"]LAMMPS[/COLOR]]("http://lammps.sandia.gov")) , you should select the correct "mpirun" to run your parallel code (see [[COLOR="Blue"]LAMPPS in Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6686836#post6686836"))

cheers 
a

---

### Post by anupamgupta on 2009-04-25
Download MPICH2 source code from [http://www-unix.mcs.anl.gov/mpi/mpich](http://www-unix.mcs.anl.gov/mpi/mpich) .

Extract .tar.bz2 file in /mirror. Also make a folder for MPICH installation.

$ mkidr mpich2
$ tar xvf mpich2-*1.0.5p3.tar.gz
$ cd mpich2*-1.0.5p3
for bash and sh:
mpich2*-1.0.5p3$ ./configure --*prefix=/mirror/mpich2 2>&1 | tee c.txt
mpich2*-1.0.5p3$ make 2>&1 | tee m.txt
mpich2*-1.0.5p3$ sudo make install 2>&1 | tee mi.txt

For more information about compilation see README file in source package.

After successfully compiling and installing mpich, add these lines to ".bashrc/"
PATH=/home/you/mpich2-install/bin:$PATH ; export PATH

for csh and tcsh:
mpich2*-1.0.5p3$ ./configure --*prefix=/mirror/mpich2 | tee c.txt
mpich2*-1.0.5p3$ make | tee m.txt
mpich2*-1.0.5p3$ sudo make install | tee mi.txt

Add the bin subdirectory of the installation directory to your path:

    for csh and tcsh:

      setenv PATH /home/you/mpich2-install/bin:$PATH

---

