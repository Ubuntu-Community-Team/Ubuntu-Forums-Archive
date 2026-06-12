---
title: "[SOLVED] mpi and fftw related problem"
date: 2007-11-08
forum: Programming Talk
---

### Post by chichilalescu on 2007-11-08
Hello all.

I'm not sure I looked everywhere I could before I came here, but I'm stuck.

Problem:

I am working with a program written in fortran90 that uses the fftw libraries, which in turn use mpi (I did not write the program).

The program compiles and runs with no problems on the lab's network of computers, but I need to run it on my laptop for various tests.

It was a little complicated to compile it on ubuntu, but I got it at one point with gfortran. To be honest, I have no idea if I am using openmpi or mpich at the moment (installed them both, and I even installed mpich with the clasical configure-make-make install next to ubuntu's installation). Additionally, I have no idea which mpi libraries the fftw uses, but I guess mpich should work (because that's what they have at the lab).

Anyway, all tests for fftw (/usr/share/doc/fftw-docs/examples/mpi) using mpi work just fine with mpirun.

The program I want to run compiles (with -fsecond-underscore added for gfortran) and links ok. I tried linking it to every mpi library I could find on my hard drive.

The program starts, outputs some (normal) messages, and it gives an error when it gets to the initialization for fftw (it's a pseudo spectral code for fluid dynamics, and it uses fft-s for each step):

[chichi-laptop:07513] *** An error occurred in MPI_Comm_dup
[chichi-laptop:07513] *** on communicator MPI_COMM_WORLD
[chichi-laptop:07513] *** MPI_ERR_COMM: invalid communicator
[chichi-laptop:07513] *** MPI_ERRORS_ARE_FATAL (goodbye)
[chichi-laptop:07510] [0,0,0]-[0,1,0] mca_oob_tcp_msg_recv: readv failed with errno=104

This last line only appeared twice until now, I guess it's connected to what combination of libraries I am using (I tried to find it somewhere on the net, and I got something that I couldn't understand).

I also know that the program runs fine on other windows, mac and linux machines, but it just won't run on my ubuntu (7.04). My next step is to install everything manually in a folder, and hope for the best, but it seems strange to need to do this.

So... help please :)

---

### Post by chichilalescu on 2007-11-17
Hello again
(I know I'm talking to myself, but just to make sure)

So... solved part of the problem. it seems fftw manages to create it's plans, but afterwards I run into trouble again, and this time it might be because of the actual program that I'm compiling (seems strange though).

Anyway:
installed g77 and gfortran ubuntu packages.
installed openmpi ubuntu package.
installed fftw from sources.
compiled own program with "gfortran -fsecond-underscoring" and everything linked ok (on a side note, why would they NOT make this a default option for gfortran?! no matter, I don't like fortran).
program went past two calls of "rfftwnd_f77_mpi_create_plan", and then got stuck somewhere:

Signal:11 info.si_errno:0(Success) si_code:1(SEGV_MAPERR)
Failing at addr:0x2b
[0] func:/usr/lib/libopal.so.0 [0xb7b15ca6]
[1] func:[0xffffe440]

When I will look into this again, I will post my discoveries, maybe someday they will be useful to someone.

On another note, I managed to make mpich (from sources, obviously) use gfortran: I uninstalled g77 and made symlinks "f77" and "f90" to gfortran. mpich creates an mpif90 that actually works (by the way, mpif90.openmpi seems to be dead), but I'm too tired now to uninstall everything and retry with the mpich/fftw combination instead of openmpi/fftw. I also have doubts that it would work, because I have no idea how to make mpif90 use the "-fsecond-underscore" option for gfortran, and I'm not sure if it can use the c functions of fftw.
Note: g77 needs to be uninstalled for this to work, because mpich checks if the f77 and f90 compilers are compatibile.

thanks for reading :)

---

### Post by meatpan on 2007-11-17
Just curious, how are you running the program?  Are you using mpirun?  I think posting your command line would give some good context.  Also, can you describe your mpi environment?  Are you running an mpi daemon?

Have you tried a simple, proof-of-concept, program in your new, local,  mpi environment?  Check out some of the examples in your mpi distribution ( I think they are under the share directory), compile them, and see how they run.   This might help you debug environment issues in a simple scenario.  If everything works well, you should have a bit more confidence debugging your f77 fft program.

---

### Post by chichilalescu on 2007-11-17
Thanks for the question. Seems the problem is using fftw with openmpi:
untill now, all tests ran fine, but i didn't take into account that untill now all fftw libraries that i used were either installed with adept, either compiled with mpich. it seems compiling fftw with openmpi is a bad idea:

chichi@chichi-laptop:/stuff/externals/fftw-2.1.5/mpi$ mpirun --mca btl ^openib -np 1 test_transpose_mpi
Signal:11 info.si_errno:0(Success) si_code:1(SEGV_MAPERR)
Failing at addr:0xcf
[0] func:/usr/lib/libopal.so.0 [0xb7dd7ca6]
[1] func:[0xffffe440]
[2] func:test_transpose_mpi [0x8049ae1]
[3] func:test_transpose_mpi [0x8048d11]
*** End of error message ***

However, test_sched works:

chichi@chichi-laptop:/stuff/externals/fftw-2.1.5/mpi$ mpirun --mca btl ^openib -np 1 test_sched
Doing infinite tests...
npes = 1...OK
npes = 2...OK
npes = 3...OK
npes = 4...OK
npes = 5...OK
npes = 6...OK
npes = 7...OK
npes = 8...OK

(it ran until over 50, and I killed it with ctrl-c).

I added the "--mca btl ^openib" in order not to fill the screen with nonsense from libibverbs and so on.
These are tests that I ran with my current configuration, openmpi/fftw. I will give you an update next week when I try again with mpich and just gfortran (tomorrow I have a train/plane/train cycle to home, so no time for playing...).

Thanks again.

---

### Post by chichilalescu on 2007-11-18
OK, I seem to be asking for the impossible.
Removed openmpi and g77.
Compiled mpich with gfortran.
Compiled fftw. All tests worked (note that fftw does not come with a fortran/mpi example, just tests for mpi).

compiled program, got linking error, went to tests for mpich, and got the same linking error:

root@chichi-laptop:/stuff/externals/mpich-1.2.7/examples/basic# /usr/bin/mpif90  -o pi3f90 pi3f90.f90
/usr/lib/libmpich.a(farg.o): In function `mpir_getarg_':
farg.f:(.text+0x2e): undefined reference to `getarg_'
collect2: ld returned 1 exit status

googled 'undefined reference to `getarg_'', and tried again using the only advice i could find (use lg2c to get rid of linking error). got another error:

root@chichi-laptop:/stuff/externals/mpich-1.2.7/examples/basic# /usr/bin/mpif90  -c pi3f90.f90
root@chichi-laptop:/stuff/externals/mpich-1.2.7/examples/basic# /usr/bin/mpif90  -o pi3f90 pi3f90.f90 -lg2c
root@chichi-laptop:/stuff/externals/mpich-1.2.7/examples/basic# ./pi3f90
 Process            0  of            1  is alive
Enter the number of intervals: (0 quits)
10
[0] MPI Internal Aborting program Deep nest in Check_incoming
[0] Deep nest in Check_incoming
p0_18202:  p4_error: : 1

I noticed that when compiling with mpich, i don't actually need to run them explicitly with mpirun, which is kind of nice (I get the same error for any number of processors that i pass to mpirun, so i just posted it once).
I found something strange yesterday, that i had no idea about:
[http://ubuntuforums.org/showpost.php?p=3621092&postcount=7](http://ubuntuforums.org/showpost.php?p=3621092&postcount=7)
I made a superficial search for namelists and gfortran, and couldn't find anything. I suppose this error I get is caused either by gfortran, either by the fact that I am linking with libg2c, which shouldn't be necessary, otherwise the people that made the tests would have added it themselves.
I should start searching for another compiler probably.

---

### Post by chichilalescu on 2007-11-23
for an update:

my program still doesn't work, still not sure why.

but just as a sideline, i got fftw to work with openmpi: when configuring, i said "./configure --enable-mpi --with-openmpi". saw it on a webpage somewhere, and i have no idea why they don't have a file where i could see all the options configure can take.
this was done with openmpi installed from ubuntu packages, and gfortran as the sole fortran compiler.

the problem that i get right now comes either from fftw or from gfortran. I will post the function that generates an error (hopefully the only one). rx, ry and rz are parameters (integers), nx is rx-1, and Ns is also a parameter (this is a 3d field, in real space kept on a grid of nx*ny*nz points, and rx is larger because fftw likes it that way i was told, ry is ny-1, and rz=nz/(number of nodes)-1.)
i would turn it all into c if it didn't use namelists for reading some parameters, and if there wasn't a problem of changing the order of indexing when going from c to fortran.

```
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!                                                          !!
!!                         ifft3ds                          !!
!!                                                          !!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
SUBROUTINE ifft3ds(fwave,freal)
  USE parameters
  USE mpi_var
  USE fftwmodule
  IMPLICIT NONE

  REAL, INTENT(IN)        :: fwave(0:rx,0:ry,0:rz)
  REAL, INTENT(OUT)       :: freal(0:rx,0:ry,0:rz)    
  REAL, ALLOCATABLE, DIMENSION(:)      :: work
  
  ALLOCATE(work(0:local_nr-1))  
  freal=fwave
  CALL rfftwnd_f77_mpi(plan_CtoR,1,freal,work,1,FFTW_TRANSPOSED_ORDER)
  freal=freal/Ns
  freal(nx:nx+1,:,:)=0.0
  
  DEALLOCATE(work)

END SUBROUTINE ifft3ds

```

if i don't call rfftwnd_f77_mpi, i get no errors. if i do, i get

```

Signal:11 info.si_errno:0(Success) si_code:1(SEGV_MAPERR)
Failing at addr:(nil)
[0] func:/usr/lib/libopal.so.0 [0xb7baeca6]
[1] func:[0xffffe440]
[2] func:/usr/lib/libgfortran.so.2(_gfortran_deallocate+0x29) [0xb7ed42f9]
[3] func:./turbo [0x804e8d2]
[4] func:./turbo [0x80499de]
[5] func:./turbo [0x80bcc27]
[6] func:/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c6b050]
[7] func:./turbo [0x80497a1]
*** End of error message ***

```

I'll try openmpi and g95 next.

---

### Post by chichilalescu on 2007-11-23
used g95 with openmpi, and got another error, for the same rfftwnd_f77_mpi:

```
Signal:11 info.si_errno:0(Success) si_code:1(SEGV_MAPERR)
Failing at addr:0xf57a1957
*** glibc detected *** ./turbo: free(): invalid next size (fast): 0x08181010 ***

```

I hate fortran.
I then used the -r8 flag for g95, and i got no error (just some memory leaks that i will look at now). it's just that gfortran has no idea what "-r8" means... whatever.
i still hate fortran.
i uninstalled g95, and reinstalled gfortran. recompiled fftw and my program, and used the "-fdefault-real-8" flag for compiling my program. the program runs fine.
(i'm depressed)

reediting: just tried to run the program with 2 processes, and it crashed again. anyway, running it with just one is better than nothing.

---

