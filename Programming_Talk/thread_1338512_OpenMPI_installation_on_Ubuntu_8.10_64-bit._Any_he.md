---
title: "OpenMPI installation on Ubuntu 8.10 64-bit. Any help?"
date: 2009-11-26
forum: Programming Talk
---

### Post by fivos on 2009-11-26
Hi to everyone,
 
I have been trying for some time to find a way to install OpenMPI on a Ubuntu 8.10 64-bit machine. I need it for practising with MPI programs in small scale before using them on an actual cluster. However I was unable to install it properly and it is unable to find the Intel C++ & fortran compilers I want to use. I have read the instruction located at the OpenMPI site. Also I have already tried posting for help at the OpenMPI site, but responses were not helpful. 
So I am asking here for help hoping that there are ubuntu users who have tried to install OpenMPI on Ubuntu and I would like them to provide with any ideas/help. 
 
So the first part was to download the .tar file from the OpenMPI website ([http://www.open-mpi.org/](http://www.open-mpi.org/)) and untar it in a directory (e.g. /home/fivos/openmpi-1.3.3). 
After that I have used the 
./configure CC=icc CXX=icpc F77=ifort FC=ifort >out.log 2> errors.log
to configure the OpenMPI installation to link OpenMPI to icc, icpc (intel C/C++ compilers) and ifort (intel fortran 77 & 95 compilers).
The output of the errors.log is :
 
configure: WARNING: -fno-strict-aliasing has been added to CFLAGS
configure: WARNING: -restrict has been added to CFLAGS
configure: WARNING: -finline-functions has been added to CXXFLAGS
configure: WARNING: MPI_REAL16 and MPI_COMPLEX32 support have been disabled
configure: WARNING: valgrind.h not found
configure: WARNING: On Linux and --with-udapl was not specified
configure: WARNING: Not building the udapl BTL
configure: WARNING: Unknown architecture ... proceeding anyway
configure: WARNING: File locks may not work with NFS. See the Installation and
users manual for instructions on testing and if necessary fixing this
configure: WARNING: -fvisibility=hidden has been added to CFLAGS
configure: WARNING: no usable BFD found; using nm-output file for addr./symbol mapping
configure: WARNING: Unrecognized options: --enable-ltdl-convenience
configure: WARNING: Unrecognized options: --enable-ltdl-convenience
 
(I am not posting the out.log because it is rather big).
 
After that I use the command : 
make all install
 
..... (lots of output) .....
 
At the end of the make procedure I get this : 
 
make[2]: *** [install-dist_amca_paramDATA] Error 1
make[2]: Leaving directory `/home/fivos/openmpi-1.3.3/contrib'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/fivos/openmpi-1.3.3/contrib'
make: *** [install-recursive] Error 1
 
 
After that the OpenMPI installation should be complete and the openMPI wrappers linked to the compilers I' ve mentioned above. But instead when I type e.g.
mpif77 I get :
 
fivos@fivos-desktop:~/openmpi-1.3.3$ mpif77
The program 'mpif77' can be found in the following packages:
* lam4-dev
* libmpich1.0-dev
* libopenmpi-dev
* libmpich-mpd1.0-dev
* libmpich-shmem1.0-dev
Try: sudo apt-get install <selected package>
bash: mpif77: command not found
 
What has gone wrong? 
I am looking forward hearing any ideas. Thank you in advance.

---

### Post by MamtaPrasad on 2012-03-16
Even Iam having the same problem.

---

