---
title: "Compiling problems with gfortran and NETCDF"
date: 2009-01-07
forum: Programming Talk
---

### Post by RobinTopper on 2009-01-07
I'm working on/with a program written in fortran that should be able to read a NETCDF file and extract some data from it. At the university I was able to compile it and run it.  
At home I had NETCDF 3.6.3 in order to get GMT working. Today I uninstalled both GMT and NETCDF, because I wanted to install the new versions of NETCDF (NETCDF 4) and GMT. Libraries are installed in /usr/lib and include files in /usr/include.

Now I'm trying to compile the fortran program with gfortan with this command (in a shell script):
[PHP]
gfortran -o /media/52GB/Atl/Input/ccsm/readCCSMnc readCCSMnc.f90 /usr/lib/libnetcdf.a -I/usr/include
[/PHP]
which is similar to the command I used at the university:
[PHP]
gfortran -o /net/home/topper/bin/Atl/Input/CCSM/readCCSMnc readCCSMnc.f90 /usr/local/netcdf-GCC/lib/libnetcdf.a -I/usr/local/netcdf-GCC/include
[/PHP]
This produces the following output:
[PHP]
robin@robin-desktop:/media/52GB/Atl/Input/ccsm$ readCCSMnc.sh
/tmp/cc6h7Eue.o: In function `MAIN__':
readCCSMnc.f90:(.text+0xfa): undefined reference to `__netcdf__nf90_open'
readCCSMnc.f90:(.text+0x158): undefined reference to `__netcdf__nf90_inq_dimid'
readCCSMnc.f90:(.text+0x1a8): undefined reference to `__netcdf__nf90_inquire_dimension'
readCCSMnc.f90:(.text+0x1ee): undefined reference to `__netcdf__nf90_inq_dimid'
readCCSMnc.f90:(.text+0x23e): undefined reference to `__netcdf__nf90_inquire_dimension'
readCCSMnc.f90:(.text+0x284): undefined reference to `__netcdf__nf90_inq_dimid'
readCCSMnc.f90:(.text+0x2d4): undefined reference to `__netcdf__nf90_inquire_dimension'
readCCSMnc.f90:(.text+0x662): undefined reference to `__netcdf__nf90_inq_varid'
readCCSMnc.f90:(.text+0x6c2): undefined reference to `__netcdf__nf90_get_var_1d_eightbytereal'
readCCSMnc.f90:(.text+0x708): undefined reference to `__netcdf__nf90_inq_varid'
readCCSMnc.f90:(.text+0x768): undefined reference to `__netcdf__nf90_get_var_1d_eightbytereal'
readCCSMnc.f90:(.text+0x7ae): undefined reference to `__netcdf__nf90_inq_varid'
readCCSMnc.f90:(.text+0x80e): undefined reference to `__netcdf__nf90_get_var_3d_fourbytereal'
readCCSMnc.f90:(.text+0x854): undefined reference to `__netcdf__nf90_inq_varid'
readCCSMnc.f90:(.text+0x8b4): undefined reference to `__netcdf__nf90_get_var_3d_fourbytereal'
readCCSMnc.f90:(.text+0xca4): undefined reference to `__netcdf__nf90_close'
/tmp/cc6h7Eue.o: In function `handle_err_':
readCCSMnc.f90:(.text+0xdd4): undefined reference to `__netcdf__nf90_strerror'
collect2: ld returned 1 exit status
[/PHP]
Apparently there is some sort of linker error at the base of the problem, but I'm quite new to working with linux and don't know how to solve this. The other problem is I don't know whether it's the uninstall/reinstall or the command that causes the problem.

I would appreciate any help with this problem.

Greetings,
Robin Topper

---

### Post by RobinTopper on 2009-01-07
Problem solved! :D

It turned out to be a problem in the compile command. The working command is
[PHP]
gfortran -o /media/52GB/Atl/Input/ccsm/readCCSMnc readCCSMnc.f90 /usr/lib/libnetcdff.a /usr/lib/libnetcdf.a -I/usr/include
[/PHP]

Anyway, thank you for reading my explanation of the problem.

---

### Post by Peirong Lin on 2012-12-17
> **RobinTopper said:**
> Problem solved! :D

It turned out to be a problem in the compile command. The working command is
[PHP]
gfortran -o /media/52GB/Atl/Input/ccsm/readCCSMnc readCCSMnc.f90 /usr/lib/libnetcdff.a /usr/lib/libnetcdf.a -I/usr/include
[/PHP]

Anyway, thank you for reading my explanation of the problem.
Hi, do you have an idea why adding "usr/lib/libnetcdf.a" would solve the problem? I also had compiling problem as yours, and solved it when I followed your reply, but I still don't know why. btw, I am newbies to Linux~ 

Thanks for reply! :)

---

