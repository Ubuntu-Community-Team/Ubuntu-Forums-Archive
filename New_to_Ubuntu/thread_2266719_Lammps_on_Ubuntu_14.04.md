---
title: "Lammps on Ubuntu 14.04"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by majid5 on 2015-02-24
Dear All,

Maybe here is not a right place to ask my question. Please accept my apologies.
I am a newcomer to Ubuntu. I am using a software called "VMware Workstation" on my laptop to install Ubuntu 14.04. Everything was fine installed with LAMMPS serial (lmp_serial). But, when I want to run LAMMPS the following error occurs

lmp_serial : command not found

Regarding to that I am not very familiar with Ubuntu, I may miss something technical issue about Ubuntu.
I really would be appreciated if anybody helps me to get rid it.

Thanks in advance

MajiD

---

### Post by Holger_Gehrke on 2015-02-25
What way did you install LAMMPS, from source or from the PPA (ppa:gladky-anton/lammps) ?

If the former, the binary is probably in a directory that's not in the $PATH. Change to the directory where the build-system put it and do './lmp_serial'.

If the latter, the executable isn't named 'lmp_serial' but 'lammps-daily' and might not work, since the build system on the PPA reports a build-failure related to some option in the make file the compiler doesn't understand ...

---

### Post by Anh_Tran on 2015-02-25
You need to download a tarball, unzip it, go to src directory and make serial.

Then run it by ./lmp_serial (or whatever binary/executable file) with this. Exception is MPI version, which you have to run with mpirun -np 2 lmp_openmpi < input_scripts if you want to run on 2 procs

// I think I just saw you on lammps-user mailing list a few weeks ago... One honest advice is if you want to be good at LAMMPS, then you have to knock your head on the computer for a few months...

---

