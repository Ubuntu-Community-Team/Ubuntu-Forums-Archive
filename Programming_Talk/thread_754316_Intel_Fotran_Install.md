---
title: "Intel Fotran Install"
date: 2008-04-13
forum: Programming Talk
---

### Post by TreeHugger52 on 2008-04-13
I am attempting to install the intel fortran compiler version 10.1.015 on a Macbook Santarosa running Gutsy.

I downloaded the tar from intel, registered for a non-commercial licence, and successfully entered my serial number when I ran install.sh. Things seemed to be going well until I got the error output in the terminal pasted below. 

The debugger seemed to install correctly afterwards (no errors), but ifort doesn't seem to be installed (sudo ifort -V resulted in 'command not found').

Any suggestions?



Pasted from the terminal...

Where do you want to install to?  Specify directory starting with '/'. 
    [/opt/intel/fc/10.1.015]   :   
--------------------------------------------------------------------------------
Intel(R) Fortran Compiler for applications running on IA-32, Version 10.1.015
Installing...
Installation successful.
--------------------------------------------------------------------------------

Testing Intel(R) Fortran compiler installed in /opt/intel/fc/10.1.015 ... 
--- ERROR ---
Binary test file /tmp/install_fc.sh6496/test_fc.6496 not found
Problems with Fortran compiler:  Output not equal to < Hello, World!  F90>[/B]
----------------------------------------------------
Contents of /tmp/install_fc.sh6496/test_fc.6496.log:
test_fc - /opt/intel/fc/10.1.015 - Sun Apr 13 15:49:05 CDT 2008
ifort found in /opt/intel/fc/10.1.015/bin/ifort
ifort -V output:
Intel(R) Fortran Compiler for applications running on IA-32, Version 10.1    Build 20080312 Package ID: l_fc_p_10.1.015
Copyright (C) 1985-2008 Intel Corporation.  All rights reserved.
FOR NON-COMMERCIAL USE ONLY

/opt/intel/fc/10.1.015/bin/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifort: error #10257: Fatal error in /opt/intel/fc/10.1.015/bin/fortcom, terminated by 0x7f
----------------------------------------------------
Problems with Fortran compiler: <file not found>!=< Hello, World!  F90>

---

### Post by LaRoza on 2008-04-13
Try:

```

sudo aptitude install build-essential

```

---

### Post by TreeHugger52 on 2008-04-14
I did, but aptitude didn't make any changes- I was already up to date. I tried reinstalling afterwards and got the same issue.

It looks like the install file from Intel didn't include one of its own libraries, right?

---

### Post by Zwack on 2008-04-14
> **TreeHugger52 said:**
> 
/opt/intel/fc/10.1.015/bin/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Looks like you need libstdc++.so.5 installed... It's available in synaptic, but libstdc++6 is the latest.

Go, install it then try.

Z.

---

### Post by triathman on 2008-06-02
Ubuntu 8.04, Intel Fortran 10.1.15

I had the same problem, but the installation has been completed. 

Solved with  sudo apt-get install libstdc++.so.5

then 

One possibility to use ifort is to copy the file ifort from the directory where you install it (default /opt/intel/fc/10.1.15/bin) to the directory where you need to compile the program, and type in such directory a fast ./ifort *.f (for example) 

hope that this helps

---

### Post by crazychopsticks on 2008-06-15
There is a better solution assuming you got it working.

Make a link to the ifort executable from your /usr/bin/ directory. Then any user will be able to use it.

Assuming you used defaults install it will be something like:

sudo ln /opt/intel/fc/10.../bin/ifort /usr/bin/ifort

Replace with the correct version or use tab to complete the line for you.

---

### Post by netCDwtF on 2008-07-30
> **triathman said:**
> Ubuntu 8.04, Intel Fortran 10.1.15

I had the same problem, but the installation has been completed. 

Solved with  sudo apt-get install libstdc++.so.5



Do i need a CD for it >.< ?

```
ilja@jali:~$ sudo apt-get install libstdc++.so.5
[sudo] password for ilja: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++.so.5

```

worked with 
sudo apt-get install libstdc++5
:/
shal see if it works

---

### Post by Pyrrhias on 2008-08-25
I have the following problem when I compile the sample "Hello Word" with ifort.
/opt/intel/fc/10.1.018/lib/libifcore.a(for_main.o): In function `main':
for_main.c:(.text+0x28): undefined reference to `MAIN__'

I try to use the option -nofor-main and I obtain the same error. 

I have no idea how to solve this problem!

If someone has an idea I will be happy

Thanks.

---

### Post by netCDwtF on 2008-08-25
yep,  i got same error today also while compileing GETM
```

ifort -o getm_prod_IFORT getm/main.o -DIFORT -DFORTRAN95 -DREAL_4B=real\(4\) -DPRODUCTION  -O3 -i-static  -module /home/victor/GETM/tgetm/getm-stable/modules/IFORT -I/home/victor/GETM/tgetm/getm-stable/include -I/home/victor/GETM/tgetm/getm-stable/modules/IFORT -I/home/victor/GETM/gotm-4.0.0/modules/IFORT -I/usr/local/netcdf3/include -w95 -L/home/victor/GETM/tgetm/getm-stable/lib/IFORT -L/home/victor/GETM/gotm-4.0.0/lib/IFORT -lgetm_prod -loutput_prod -ldomain_prod -lmeteo_prod -l2d_prod -l3d_prod -ldomain_prod -linput_prod -lncdfio_prod -lfutils_prod  -lturbulence_prod -lutil_prod  /usr/local/netcdf3/lib/libnetcdf.a
/opt/intel/fce/10.1.015/lib/for_main.o(.text+0x26): In function `main':
: undefined reference to `MAIN__'
make: *** [getm_prod_IFORT] Error 1

```

---

### Post by tnmydas on 2009-07-13
I am getting the same problem in installing one package (*f programs) only, while the several other packages (*.f) complied successfully.  I have tried installing several libraries, but always getting the same error. The error message is :

ifort -O2  MAIN/lm.o -o lm.run  
/opt/intel/Compiler/11.0/083/lib/intel64/for_main.o: In function `main':
/export/users/nbtester/efi2linux_nightly/branch-11_0/20090319_000000/libdev/frtl/src/libfor/for_main.c:(.text+0x38): undefined reference to `MAIN__'
make: *** [lm.run] Error 1


I will appreciatete any help.
Tanmoy.

---

### Post by Sir Beaver on 2010-03-31
For me, sudo apt-get install libstdc++5 did not work 
on Ubuntu 9.10. I got ifort to work by following the instructions
on [http://ubuntuforums.org/showthread.php?t=586247](http://ubuntuforums.org/showthread.php?t=586247) 
where they tell how to do a manual installation of the 
library.

---

### Post by oceanid on 2010-04-20
> **netCDwtF said:**
> yep,  i got same error today also while compileing GETM
```

ifort -o getm_prod_IFORT getm/main.o -DIFORT -DFORTRAN95 -DREAL_4B=real\(4\) -DPRODUCTION  -O3 -i-static  -module /home/victor/GETM/tgetm/getm-stable/modules/IFORT -I/home/victor/GETM/tgetm/getm-stable/include -I/home/victor/GETM/tgetm/getm-stable/modules/IFORT -I/home/victor/GETM/gotm-4.0.0/modules/IFORT -I/usr/local/netcdf3/include -w95 -L/home/victor/GETM/tgetm/getm-stable/lib/IFORT -L/home/victor/GETM/gotm-4.0.0/lib/IFORT -lgetm_prod -loutput_prod -ldomain_prod -lmeteo_prod -l2d_prod -l3d_prod -ldomain_prod -linput_prod -lncdfio_prod -lfutils_prod  -lturbulence_prod -lutil_prod  /usr/local/netcdf3/lib/libnetcdf.a
/opt/intel/fce/10.1.015/lib/for_main.o(.text+0x26): In function `main':
: undefined reference to `MAIN__'
make: *** [getm_prod_IFORT] Error 1

```


hi
I am imaginer in linux and I need to compile GETM , would you help me please?

this is my email address: [email]apt.man@gmail.com[/email]

best regards

---

