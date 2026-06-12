---
title: "Installing Intel Libraries and Compilers"
date: 2013-05-05
forum: Programming Talk
---

### Post by Chris Bright on 2013-05-05
Hi everybody!

My machine is a Linux 64 bit laptop with Intel Core i7 cpu.

I need to install a software called Quantum Espresso  ([http://www.quantum-espresso.org/](http://www.quantum-espresso.org/)), very useful for ab-initio  simulations. Here the prerequisites:

- Fortran and C compilers
- Fortran and C MPI compilers
- MPI library
- BLAS, LAPACK and FFTW ([http://www.fftw.org/](http://www.fftw.org/)) libraries

If something is not clear, you can find the list of the prerequisites here:

[http://www.quantum-espresso.org/wp-c...ser_guide.html]("http://www.quantum-espresso.org/wp-content/uploads/Doc/user_guide/user_guide.html")

in section 2 (installation).


I had already installed the gfortran and gcc compilers but i read that   the Intel's compilers may improve the performance, so I installed Intel   Fortran Composer XE 2013, which includes the ifort compiler and MKL   library. Later, I found in the non-commercial section of Intel website  ([http://software.intel.com/en-us/non-...re-development]("http://software.intel.com/en-us/non-commercial-software-development"))   that it is also possible to download Intel Parallel Studio XE 2013,   which contains both the Fortran and the C compilers, plus the MKL, plus   some tools for parallel computing  ([http://software.intel.com/en-us/inte...llel-studio-xe]("http://software.intel.com/en-us/intel-parallel-studio-xe")). 

Here, the list of all my doubt:

**1)** Is it possible to erase the entire folder  (/opt/intel) in  which I saved Intel Composer (the folder did not exist  before) in order  to later re-create it for installing Parallel Studio?  Such an  operation will totally remove Composer from my system?

**2)** Does Intel Parallel Studio contain the MPI library  and the MPI compilers? I tried to understand from the website  ([http://software.intel.com/en-us/inte...llel-studio-xe]("http://software.intel.com/en-us/intel-parallel-studio-xe")) but it is not  clear to me.

**3)** Does MKL contain the FFTW library? I read  ([http://software.intel.com/en-us/arti...tw3-interfaces]("http://software.intel.com/en-us/articles/intel-mkl-main-libraries-contain-fftw3-interfaces"))  that it contains the FFTW3 interfaces, but I am not an expert and I do  not really understand if it is the same thing or not.


I will be very thankful to whoever will give an answer to even just one of these three points!  :grin:

---

