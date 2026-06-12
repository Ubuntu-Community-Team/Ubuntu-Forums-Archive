---
title: "OpenMPI bug"
date: 2008-04-21
forum: Programming Talk
---

### Post by vrotival on 2008-04-21
Hello everyone

Sorry to bother you all about that but I am quite lost with a puzzling problem concerning openMPI + Ubuntu 7.10

I have been designing complex openMPI program with Intel Fortran compiler for quite some time, and everything worked perfectly until this morning, when everything seemed to fall apart.

Basically, if I try now even the (very very) simple program below in Fortran 90

****************************************************
program test
  use mpi
  
  integer :: mpi_err

  call mpi_init(mpi_err)

  print *, "HELLO", mpi_err

  call mpi_finalize(mpi_err)
  
end program test
***************************************************

This code will compile (mpif90 -o test test_mpi.f90), but gives error messages at the level of MPI_INIT, whether I call it with 
> ./test
or
> mpirun -np N test

vrotival@vrotival-laptop:~/Work/workbench$ ./test
[vrotival-laptop:06375] *** Process received signal ***
[vrotival-laptop:06375] Signal: Segmentation fault (11)
[vrotival-laptop:06375] Signal code: Address not mapped (1)
[vrotival-laptop:06375] Failing at address: 0x8
[vrotival-laptop:06375] [ 0] [0xffffe440]
[vrotival-laptop:06375] [ 1] /usr/lib/libmpi.so.0(ompi_proc_init+0x13b) [0xb7f0863b]
[vrotival-laptop:06375] [ 2] /usr/lib/libmpi.so.0(ompi_mpi_init+0x10c) [0xb7f09fbc]
[vrotival-laptop:06375] [ 3] /usr/lib/libmpi.so.0(MPI_Init+0xab) [0xb7f2b22b]
[vrotival-laptop:06375] [ 4] /usr/local/lib/libmpi_f77.so.0(PMPI_INIT+0x32) [0xb7fd78d2]
[vrotival-laptop:06375] [ 5] ./test(MAIN__+0x24) [0x804dfe4]
[vrotival-laptop:06375] [ 6] ./test(main+0x3d) [0x804dfb1]
[vrotival-laptop:06375] [ 7] /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7a39050]
[vrotival-laptop:06375] [ 8] ./test [0x804df11]
[vrotival-laptop:06375] *** End of error message ***




I am using openMPI version 1.2.6 (but same bug occured with 1.2.5), which I compile directly from the source from [www.openmpi.org](www.openmpi.org), with F90=ifort with Intel Fortran 10.1
I have not updated ifort since about 6 months, the only change between last time I used MPI are small Ubuntu updates..... I can give you much more complex codes which worked perfectly one week ago

As a small comment, the ouput from ompi_info is also weird

vrotival@vrotival-laptop:~/Work/workbench$ ompi_info --all
ompi_info: Symbol `mca_allocator_base_components' has different size in shared object, consider re-linking
ompi_info: symbol lookup error: ompi_info: undefined symbol: ompi_mtl_base_components_opened

but I hadn't looked at it before the bug





Has anyone else encountered this bug ? can it be relaed to recent updates in Ubuntu (although I do not want to incriminate it at first)

I am upgrading my Ubuntu with the following repositories

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted


If anyone has any advice it would be greatly appreciated (and would save my PhD as a byproduct ](*,)](*,)](*,))

Cheers !

---

### Post by ilmarw on 2008-04-30
Yes, I have had the same bug. Using the packages from debian sid fixed it, but I have not yet determined the cause. We should file a bug report. I have been waiting for a long time now for the openmpi package to work properly in Ubuntu, and thought it finally might be fixed now. I really need it to.

Edit: might have been a bit quick here. Your test program ran, but the error looked very similar to mine:
[multiboot:28166] *** Process received signal ***
[multiboot:28166] Signal: Segmentation fault (11)
[multiboot:28166] Signal code: Address not mapped (1)
[multiboot:28166] Failing at address: 0x8854004
[multiboot:28166] [ 0] [0xb7f3d440]
[multiboot:28166] [ 1] /usr/lib/libopen-pal.so.0(free+0xc4) [0xb5aebae4]
[multiboot:28166] [ 2] /usr/lib/libopen-pal.so.0 [0xb5ad1d3e]
[multiboot:28166] [ 3] /usr/lib/libopen-pal.so.0 [0xb5ad18ea]
[multiboot:28166] [ 4] /usr/lib/libopen-pal.so.0(lt_dlforeachfile+0x3d) [0xb5ad19dd]
[multiboot:28166] [ 5] /usr/lib/libopen-pal.so.0(mca_base_component_find+0x327) [0xb5ada1d7]
[multiboot:28166] [ 6] /usr/lib/libopen-pal.so.0(mca_base_components_open+0x18a) [0xb5adabca]
[multiboot:28166] [ 7] /usr/lib/libopen-pal.so.0(opal_memory_base_open+0x44) [0xb5aea3c4]
[multiboot:28166] [ 8] /usr/lib/libopen-pal.so.0(opal_init+0x9a) [0xb5acf63a]
[multiboot:28166] [ 9] /usr/lib/libmpi.so.0(ompi_mpi_init+0x19) [0xb5b9e2b9]
[multiboot:28166] [10] /usr/lib/libmpi.so.0(MPI_Init+0xe7) [0xb5bc1587]
[multiboot:28166] [11] /usr/lib/libpetsc.so.2.3.3(PetscInitialize+0x251) [0xb68428ce]
[multiboot:28166] [12] /tmp/lib/libdolfin.so(_ZN6dolfin17SubSystemsManager9initPETScEiPPcb+0x98) [0xb5d6a2c8]
[multiboot:28166] [13] /tmp/lib/libdolfin.so(_ZN6dolfin17SubSystemsManager9initPETScEv+0xaf) [0xb5d6a44f]
[multiboot:28166] [14] /tmp/lib/libdolfin.so(_ZN6dolfin11PETScMatrixC1ENS0_4TypeE+0x27) [0xb5d5f3d7]
[multiboot:28166] [15] /tmp/lib/python2.5/site-packages/dolfin/_dolfin.so [0xb6f7a1ab]
[multiboot:28166] [16] python(PyObject_Call+0x27) [0x805cb37]
[multiboot:28166] [17] python(PyEval_EvalFrameEx+0x4064) [0x80c7ce4]
[multiboot:28166] [18] python(PyEval_EvalCodeEx+0x6e7) [0x80cb0d7]
[multiboot:28166] [19] python [0x8113430]
[multiboot:28166] [20] python(PyObject_Call+0x27) [0x805cb37]
[multiboot:28166] [21] python [0x8062b9b]
[multiboot:28166] [22] python(PyObject_Call+0x27) [0x805cb37]
[multiboot:28166] [23] python [0x809d26b]
[multiboot:28166] [24] python [0x809ee64]
[multiboot:28166] [25] python(PyObject_Call+0x27) [0x805cb37]
[multiboot:28166] [26] python(PyEval_EvalFrameEx+0x3d07) [0x80c7987]
[multiboot:28166] [27] python(PyEval_EvalCodeEx+0x6e7) [0x80cb0d7]
[multiboot:28166] [28] python(PyEval_EvalFrameEx+0x565e) [0x80c92de]
[multiboot:28166] [29] python(PyEval_EvalCodeEx+0x6e7) [0x80cb0d7]
[multiboot:28166] *** End of error message ***
Segmentation fault


ilmar

---

### Post by Adversus on 2008-05-20
I'm having a similar problem, a code that compiled and ran fine before now causes the above errors.. I have no idea what is causing it, it is possible that the package fftw (2.1.5 version, compiled with mpi support) is causing the problems. It happens when the package is compiled with openmpi (giving the above error messages) as well as with lam mpi (just telling me there is a segfault).

---

### Post by vrotival on 2008-05-20
Okay I solved the bug, at least for me, by removing with apt-get remove EVERYTHING related to openmpi / mpich... then doing a clean install from scratch from the openmpi sources 

Hope this will help you too

---

