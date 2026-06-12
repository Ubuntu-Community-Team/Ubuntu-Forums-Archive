---
title: "compiling a script for climate data modeling"
date: 2018-05-30
forum: Packaging and Compiling Programs
---

### Post by atef41dz on 2018-05-30
Hi everyone,

I am trying to compile a script that requires NetCDF and HDF5 libraries. After installing both, I navigate the folder containing the code and type "make" and get the following error message. I am quite new to to Ubuntu unfortunately and would appreciate any help understanding and solving the problem. THANK YOU


```
________________________________________________________________________________ ERROR MESSAGE ___________________________________________________________

root@atef1-VirtualBox:/media/atef1/Seagate/workcopy/downscaling_code/day_to_3hr# make
make utils/libutils.a; make model
make[1]: Entering directory '/media/atef1/Seagate/workcopy/downscaling_code/day_to_3hr'
make[1]: 'utils/libutils.a' is up to date.
make[1]: Leaving directory '/media/atef1/Seagate/workcopy/downscaling_code/day_to_3hr'
make[1]: Entering directory '/media/atef1/Seagate/workcopy/downscaling_code/day_to_3hr'
gcc -o downscale downscale.o make_dmy.o mtclim42_vic.o mtclim42_wrapper.o svp.o vicerror.o nrerror.o calc_longwave.o calc_air_temperature.c alloc_atmos.c calc_forcing_stats.o nc_utils.o  -I. -Iutils -fopenmp -O3 -Wall -Lutils -lutils -lnetcdf -lm
calc_air_temperature.c:6:13: warning: ‘vcid’ defined but not used [-Wunused-variable]
 static char vcid[] = "$Id: calc_air_temperature.c,v 4.2 2006/10/31 01:18:42 vicadmin Exp $";
             ^~~~
alloc_atmos.c:19:13: warning: ‘vcid’ defined but not used [-Wunused-variable]
 static char vcid[] = "$Id: alloc_atmos.c,v 5.5.2.4 2010/10/05 20:38:23 vicadmin Exp $";
             ^~~~
/usr/bin/x86_64-linux-gnu-ld: downscale.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: make_dmy.o: relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: mtclim42_vic.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: mtclim42_wrapper.o: relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: vicerror.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: nrerror.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: calc_forcing_stats.o: relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: nc_utils.o: relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: utils/libutils.a(array.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: utils/libutils.a(utils.o): relocation R_X86_64_32S against `.rodata.str1.1' can not be used when making a PIE object; recompile with -fPIC
/usr/bin/x86_64-linux-gnu-ld: final link failed: Nonrepresentable section on output
collect2: error: ld returned 1 exit status
Makefile:40: recipe for target 'model' failed
make[1]: *** [model] Error 1
make[1]: Leaving directory '/media/atef1/Seagate/workcopy/downscaling_code/day_to_3hr'
Makefile:28: recipe for target 'all' failed
make: *** [all] Error 2
```

---

### Post by &amp;KyT$0P# on 2018-05-30
As the error messages say, you need to try adding [FONT=Courier New]-fPIC[/FONT] to the C compiler flags and/or C++ compiler flags.  If that does not work, try instead adding [FONT=Courier New]-fno-PIE -no-pie[/FONT] to the C compiler flags and C++ compiler flags.

How to do this will depend on the specific software.

---

### Post by xadder on 2018-06-08
netcdf (and related packages such as nco, cdo) were available in the repos in 17.10, so installation was trivial. I can't find them in the 18.04 repos though. If they are available somewhere, you could just install with apt-get.

More generally, does anyone know what happened to these packages. They are critical for all kinds of climate and meteorology work.

---

### Post by oldfred on 2018-06-08
Looking in synaptic with just 'netcdf',which is what you should be using shows many related apps.

There is cdftools, , cdo, and python, ruby, R apps from netcdf. Many  other related programs or data analysis tools.

If you do not have synaptic.
sudo apt install synaptic

---

