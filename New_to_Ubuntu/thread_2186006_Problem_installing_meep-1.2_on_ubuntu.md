---
title: "Problem installing meep-1.2 on ubuntu"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by assood1991 on 2013-11-05
Hi Guys,
I am facing a problem that I have been stuck with for the past couple of days. I am trying to install meep-1.2 on ubuntu. The software requires a few other additional packages and compilers such as blas, lapack, libctl, etc. I am hoping I installed successfully all the prerequisits required by the developers.
I downloaded meep on desktop from the following link:  [http://ab-initio.mit.edu/wiki/index.php/Meep_download](http://ab-initio.mit.edu/wiki/index.php/Meep_download)    extracted it and  ran it through the normal process which they suggested ./configure ... install... make install. However I got stuck in the second step. I included the results of the first and second steps

> assood@ubuntu:~$ cd ~/Downloads/meep-1.2
assood@ubuntu:~/Downloads/meep-1.2$ sudo ./configure
[sudo] password for assood: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for C++ compiler vendor... gnu
checking whether C++ compiler accepts -malign-double... yes
checking whether C++ compiler accepts -fstrict-aliasing... yes
checking whether C++ compiler accepts -ffast-math... yes
checking for gcc architecture flag... 
checking for x86 cpuid 0 output... d:756e6547:6c65746e:49656e69
checking for x86 cpuid 1 output... 206d7:1020800:9eba2203:1fabfbff
checking whether C++ compiler accepts -march=native... yes
checking for gcc architecture flag... -march=native
checking whether C++ compiler accepts -O3 -malign-double -fstrict-aliasing -march=native... yes
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for latex2html... no
configure: WARNING: Cannot find latex2html in your path!
checking for sin in -lm... yes
checking for fftw_plan_dft_1d in -lfftw3... no
checking for fftw_create_plan in -ldfftw... no
checking for fftw_create_plan in -lfftw... no
configure: WARNING: FFTW needed for MPB
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking whether we are using the GNU Fortran 77 compiler... (cached) yes
checking whether g77 accepts -g... (cached) yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... no
checking if g77 supports -c -o file.o... yes
checking if g77 supports -c -o file.o... (cached) yes
checking whether the g77 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking how to get verbose linking output from g77... -v
checking for Fortran 77 libraries of g77...  -L/usr/lib/gcc/x86_64-linux-gnu/3.4.6 -L/usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../../../lib -L/usr/lib/gcc/x86_64-linux-gnu/3.4.6/../../.. -L/lib/../lib -L/usr/lib/../lib -lfrtbegin -lg2c -lm
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... lower case, underscore, extra underscore
checking for sgemm_... no
checking for ATL_xerbla in -latlas... no
checking for sgemm_ in -lblas... yes
checking for dgemm_ in -ldgemm... no
checking for sgemm_ in -lmkl... no
checking for sgemm_... (cached) no
checking for sgemm_ in -lcxml... no
checking for sgemm_ in -ldxml... no
checking for sgemm_ in -lscs... no
checking for sgemm_ in -lcomplib.sgimath... no
checking for sgemm_ in -lblas... (cached) yes
checking for sgemm_ in -lessl... no
checking for sgemm_ in -lblas... (cached) yes
checking for cheev_... no
checking for cheev_ in -llapack... yes
checking for pkg-config... /usr/bin/pkg-config
checking for harminv >= 1.1... checking for harminv_get_freq_error in -lharminv... no
configure: WARNING: harminv support is disabled
checking mpb.h usability... no
checking mpb.h presence... no
checking for mpb.h... no
checking for cblas_cgemm... no
checking for cblas_cgemm in -lgslcblas... no
checking for gsl_sf_bessel_Jn in -lgsl... no
configure: WARNING: Missing GNU GSL library...Bessel-function field initialization will not be supported.
checking for deflate in -lz... yes
checking for H5Pcreate in -lhdf5... no
configure: WARNING: Couldn't find the HDF5 library!!  Switching to --without-hdf5.
checking for guile-config... guile-config
checking if linking to guile works... yes
checking libguile.h usability... yes
checking libguile.h presence... yes
checking for libguile.h... yes
checking guile/gh.h usability... no
checking guile/gh.h presence... no
checking for guile/gh.h... no
checking for scm_make_smob_type... yes
checking for SCM_SMOB_PREDICATE... no
checking for SCM_SMOB_DATA... no
checking for SCM_NEWSMOB... no
checking how to activate readline in Guile... ice-9 readline
checking for libctl dir... /usr/local/share/libctl
checking for gen-ctl-io... gen-ctl-io
checking for ctl_get_vector3 in -lctl... yes
checking ctl.h usability... yes
checking ctl.h presence... yes
checking for ctl.h... yes
checking whether libctl version is at least 3.2.0... ok
checking for libctl_quiet feature... yes
checking for basename in -lgen... no
checking for feenableexcept... yes
checking whether feenableexcept declaration is usable... yes
checking whether to catch and ignore SIGFPE signals... no
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for BSDgettimeofday... no
checking for gettimeofday... yes
checking for cblas_ddot... no
checking for cblas_daxpy... no
checking for C/C++ restrict keyword... __restrict
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating meep-pkgconfig
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating examples/Makefile
config.status: creating libctl/Makefile
config.status: creating libctl/meep.scm
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

> assood@ubuntu:~/Downloads/meep-1.2$ install
install: missing file operand
Try `install --help' for more information.
assood@ubuntu:~/Downloads/meep-1.2$

Basically, I don't understand the error > missing file operand, grateful for any help :)
Please execuse my modest skills in linux.

---

