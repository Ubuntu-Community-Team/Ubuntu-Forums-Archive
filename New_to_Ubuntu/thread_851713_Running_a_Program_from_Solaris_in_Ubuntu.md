---
title: "Running a Program from Solaris in Ubuntu"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Dahaka14 on 2008-07-06
I have Ubuntu Hardy, and I was wondering if I could take the source code of some programs from my old Solaris workstation and run them on my Ubuntu laptop.  My professor says that I need a special Solaris compiler that I have to buy.  Wouldn't I just need a compiler for the FORTRAN code?  If I need something for Solaris, could I run it in OpenSolaris?  Is there a way to run this FORTRAN program from Solaris in Ubuntu?  Let me know if you need more information.  Thanks.

---

### Post by sdennie on 2008-07-06
You could try to compile the program with g77 (gnu Fortran 77 compiler).  However, if I remember right, the Sun Fortran compiler went all Fortran 90 a few years ago so, the code may not be standard F77, it may have ignored OpenMP directives in it, etc...

If that doesn't work, rather than installing Solaris, I believe you can use VirtualBox or VMware to install a virtual machine with Solaris.

---

