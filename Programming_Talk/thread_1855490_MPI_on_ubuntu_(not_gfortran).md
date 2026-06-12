---
title: "MPI on ubuntu (not gfortran)"
date: 2011-10-06
forum: Programming Talk
---

### Post by OnkelTom on 2011-10-06
Hi,

I have a Fortran 90 code written in MPI that I usually run on a cluster. 
For small test runs I would like to run it on my Ubuntu desktop. 
The code doesn't work with gfortran so I need a free fortran compiler that will work on Ubuntu. Also, I need to have MPI installed to get it to run (even if I just want to use one core).

1) Are there any other free Fortran compilers that are compatible with Ubuntu that would suit my needs? 

2) What MPI should I install to work with the above?

  (Could anyone guide me through the installation process please for the above two items).

3) If I had an MPI programme installed, could I use a "quad core" processor as 4 nodes (really showing my ignorance of parallel computing here!) 

Cheers,

OT

---

### Post by karlson on 2011-10-06
> **OnkelTom said:**
> Hi,

I have a Fortran 90 code written in MPI that I usually run on a cluster. 
For small test runs I would like to run it on my Ubuntu desktop. 
The code doesn't work with gfortran so I need a free fortran compiler that will work on Ubuntu. Also, I need to have MPI installed to get it to run (even if I just want to use one core).

1) Are there any other free Fortran compilers that are compatible with Ubuntu that would suit my needs? 

2) What MPI should I install to work with the above?
  (Could anyone guide me through the installation process please for the above two items).


start here:
[http://www.open-mpi.org/](http://www.open-mpi.org/)

That has both libraries and the compiler wrappers for MPI.

---

### Post by Claus7 on 2011-10-06
> **OnkelTom said:**
> Hi,

I have a Fortran 90 code written in MPI that I usually run on a cluster. 
For small test runs I would like to run it on my Ubuntu desktop. 
The code doesn't work with gfortran so I need a free fortran compiler that will work on Ubuntu. Also, I need to have MPI installed to get it to run (even if I just want to use one core).

1) Are there any other free Fortran compilers that are compatible with Ubuntu that would suit my needs? 

2) What MPI should I install to work with the above?

  (Could anyone guide me through the installation process please for the above two items).

3) If I had an MPI programme installed, could I use a "quad core" processor as 4 nodes (really showing my ignorance of parallel computing here!) 

Cheers,

OT

1) You can use intel's fortran compiler. Even if intel is a private company the compiler can be downloaded for free. You just have to give a mail and you will receive some update notes. It does a good job and it has differences with gfortran.

2) I haven't tried fortran with mpi. I do know though that there are fortran compilers which compile parallel code of fortran. Have in mind that this an entirely different story, than writing a serial code. In order to install intel's fortran is straightforward. If you do not find info in these forums (there are a lot) post here again.

3)yes!

Regards!

---

### Post by OnkelTom on 2011-10-07
Hi Guys,

Thanks for that. The nudge in the right direction for both intels compilers and open MPI was enough. Managed to get it working in only a few hours so I'm chalking it as a win since my computer knowledge is pretty poor!

Right, now to crunch some numbers without having to wait in a queue on a cluster :D

Cheers,

 OT

---

