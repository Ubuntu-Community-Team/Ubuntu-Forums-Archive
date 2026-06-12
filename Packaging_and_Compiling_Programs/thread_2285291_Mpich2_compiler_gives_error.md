---
title: "Mpich2 compiler gives error"
date: 2015-07-04
forum: Packaging and Compiling Programs
---

### Post by samuel33 on 2015-07-04
Hey community,

I am pretty new here but well i hope to learn. 

I am trying to install a Open Src software (delft3d) which needs to be compiled. I already downloaded with the help of manuals and tutorials all the libs and compilers and am trying to run the build.sh. It seems to me as if the path to my mpich2 compiler is not correct. ( im typing ```
./build.sh -gnu -64bit 
``` and get an error Make fails! )

The logs file shows:

```
checking for openmpif90... /opt/mpich2-1.4.1-gcc-4.6.2/bin/mpif90
         checking for mpif.h...no 
         ./configure: line 26420: /opt/mpich2-1.4.1-gcc-4.6.2/bin/mpif90: No such file or directory 
``` 

does this mean that mpif90 just cannot be found or that i haven't installed it?

---

### Post by samuel33 on 2015-07-07
So I managed to add the right path in the build.sh file... 
For the compilation I can run a autogen.sh file and then ./configure which looks gret so far, but then the final step make gives an error again:

[HTML]use netcdf
        1
Fatal Error: Can't open module file 'netcdf.mod' for reading at (1): No such file or directory
Makefile:504: recipe for target 'datagroups.lo' failed
make[6]: *** [datagroups.lo] Error 1
make[6]: Leaving directory '/home/numericpc/trunk/src/engines_gpl/flow2d3d/packages/data/src/basics'
Makefile:482: recipe for target 'install-recursive' failed
make[5]: *** [install-recursive] Error 1
make[5]: Leaving directory '/home/numericpc/trunk/src/engines_gpl/flow2d3d/packages/data/src'
Makefile:478: recipe for target 'install-recursive' failed
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory '/home/numericpc/trunk/src/engines_gpl/flow2d3d/packages/data'
Makefile:488: recipe for target 'install-recursive' failed
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory '/home/numericpc/trunk/src/engines_gpl/flow2d3d/packages'
Makefile:478: recipe for target 'install-recursive' failed
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory '/home/numericpc/trunk/src/engines_gpl/flow2d3d'
Makefile:482: recipe for target 'install-recursive' failed
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory '/home/numericpc/trunk/src/engines_gpl'
Makefile:538: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1[/HTML]

Now i was searching for that netcdf.mod  file and found it on my system under /usr/include/netcdf.mod

How can I fix this now, do i somehow have to include this file and if where?

---

### Post by oldos2er on 2015-07-07
Moved to Packaging & Compiling Programs.

---

