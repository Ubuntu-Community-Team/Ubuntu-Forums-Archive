---
title: "cannot find -lgfotranbegin"
date: 2010-12-16
forum: Packaging and Compiling Programs
---

### Post by mons00n on 2010-12-16
Hi everyone, I'm trying to compile a fortran/c program and have run into the following error:

```

gfortran -ffixed-line-length-0 -O -fno-backslash -m32 -L/usr/share/X11  dbh.o polardens.o bulgepotential.o totdens.o halopotential.o pot.o diskdens.o dens.o appdiskpot.o plgndr1.o bulgedenspsi.o halodenspsi.o gendenspsihalo.o gendenspsibulge.o polarbulgedens.o polarhalodens.o appdiskdens.o halodens.o dfhalo.o dfbulge.o erfcen.o modstamp.o force.o appdiskforce.o gendf.o getpsi.o dpolardens.o diskpotentialestimate.o halopotentialestimate.o nfwprofiles.o sersicprofiles.o -o dbh
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libgfortranbegin.a when searching for -lgfortranbegin
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.3/libgfortranbegin.a when searching for -lgfortranbegin
/usr/bin/ld: cannot find -lgfortranbegin
collect2: ld returned 1 exit status
make: *** [dbh] Error 1

```

I'm running a fresh install of 64bit 10.04 with the gfortran package installed via apt-get.  Any help you could provide would be much appreciated!

---

### Post by SevenMachines on 2010-12-17
looks like your trying to link 32bit on amd64, to do that you'll need the cross compiling gfortran installed too..

$ sudo apt-get install gfortran-multilib

Unfortunately i dont have 64 bit to test at the moment but that package should pull in the current version, which should contain libgfortranbegin.a for 32 bit

---

### Post by mons00n on 2010-12-17
> **SevenMachines said:**
> looks like your trying to link 32bit on amd64, to do that you'll need the cross compiling gfortran installed too..

$ sudo apt-get install gfortran-multilib

Unfortunately i dont have 64 bit to test at the moment but that package should pull in the current version, which should contain libgfortranbegin.a for 32 bit

I figured this was the problem but I did not know what package was needed.  This did the trick thank you very much!

---

