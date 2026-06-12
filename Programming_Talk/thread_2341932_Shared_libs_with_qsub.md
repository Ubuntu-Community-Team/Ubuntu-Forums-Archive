---
title: "Shared libs with qsub"
date: 2016-11-02
forum: Programming Talk
---

### Post by gcdiwan on 2016-11-02
I have a small Fortran code that i am trying to run on a cluster. My ./src/CMakeLists.txt reads:

```
# build executables
enable_language(Fortran)
#blas and lapack lib
set(blaslib /usr/lib64/libblas.so.3)
set(lapacklib /usr/lib64/liblapack.so.3)
#compiler flags
set (f90flags -Wpedantic -fcheck=bounds -fcheck=all -Wall -Warray-bounds -funroll-all-loops -g -fno-f2c -O0)
file(GLOB foo_src *.f90 *.f *.for)
add_executable (foo ${foo_src})
target_link_libraries (foo ${lapacklib} ${blaslib})
target_compile_options (foo PRIVATE ${f90flags})
```

The executable foo gets built correctly and ldd foo gives me list of libraries linked:
```
    linux-vdso.so.1 =>  (0x00007ffff79ff000)    
    liblapack.so.3 => /usr/lib64/liblapack.so.3 (0x00007f0242090000)
    libblas.so.3 => /usr/lib64/libblas.so.3 (0x0000003181a00000)
    libgfortran.so.3 => /opt/software/gcc/5.2.0/lib64/libgfortran.so.3 (0x00007f0241d70000)
    libm.so.6 => /lib64/libm.so.6 (0x000000352fc00000)
    libgcc_s.so.1 => /opt/software/gcc/5.2.0/lib64/libgcc_s.so.1 (0x00007f0241b43000)
    libquadmath.so.0 => /opt/software/gcc/5.2.0/lib64/libquadmath.so.0 (0x00007f0241905000)
    libc.so.6 => /lib64/libc.so.6 (0x000000352f800000)
    librt.so.1 => /lib64/librt.so.1 (0x0000003530800000)    
   
```

I could do ./foo arg1 and it gives me the output as expected. I now want to do a batch run, my script for qsub is:
```
#!/bin/bash
#
#$ -V
#$ -cwd
#$ -j y
#$ -S /bin/bash
#$ -o test.OUT
#$ -N test
#

date
typeset -i i END
let END=10 i=1 M=1
while ((i<=END)); do
    echo "m=" $M        
        ./build/src/foo $M
        M=$((M+1))
    let i++
done
sleep 1
date
```

This however results in:

```
m= 1
./build/src/foo: error while loading shared libraries: liblapack.so.3: cannot open shared object file: No such file or directory
```.
I am not sure why this happens. My LD_LIBRARY_PATH is
```
/opt/software/gcc/5.2.0/lib64:/opt/gridengine/lib/linux-x64:/opt/openmpi/lib:/usr/lib64
```
and my /etc/ld.so.conf reads:
```
include ld.so.conf.d/*.conf
/lib64
/usr/lib64
/usr/kerberos/lib64
```
I don't understand what I am doing wrong :(
----
gcc --version
gcc (GCC) 5.2.0
gfortran --version
GNU Fortran (GCC) 5.2.0
cat /proc/version
Linux version 2.6.32-504.16.2.el6.x86_64 (mockbuild@c6b9.bsys.dev.centos.org) (gcc version 4.4.7 20120313 (Red Hat 4.4.7-11) (GCC) ) #1 SMP Wed Apr 22 06:48:29 UTC 2015

---

### Post by gcdiwan on 2016-11-02
I was not aware that qsub submits the job from main node to compute nodes. Adding ldd foo in my qsub script now shows that the libraries are only installed on main node and not on compute node. Installing the missing libs on compute node solved the problem.

---

