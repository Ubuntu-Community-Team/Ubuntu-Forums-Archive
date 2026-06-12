---
title: "Problems installing the Atom package within Siest 2.02"
date: 2009-03-07
forum: Programming Talk
---

### Post by phillip_peters52 on 2009-03-07
Hi

I am trying to install Siesta on a machine with the following spec:

Proccesor=Intel core 2 Duo Q6600
Ram=4gb
OS=Ubuntu 8.1
Compilers=g95,g77,ifort

I am able to make the main Siesta package and run the test files within the test directory.

I then follow the instructions within the quick start guide to generate a water molecule and making the pseudopotentials using the Atom package which comes with Siesta and I get the following error whilst trying to compile Atom:

xc.o: In function `ldaxc_':
xc.f:(.text+0x1a43): undefined reference to `s_cmp'
xc.f:(.text+0x1a62): undefined reference to `s_cmp'
xc.f:(.text+0x1a81): undefined reference to `s_cmp'
xc.f:(.text+0x1aa0): undefined reference to `s_cmp'
xc.f:(.text+0x1b02): undefined reference to `s_cmp'
xc.o:xc.f:(.text+0x1b21): more undefined references to `s_cmp' follow
xc.o: In function `ldaxc_':
xc.f:(.text+0x1b6a): undefined reference to `s_wsle'
xc.f:(.text+0x1b88): undefined reference to `do_lio'
xc.f:(.text+0x1ba3): undefined reference to `do_lio'
xc.f:(.text+0x1bad): undefined reference to `e_wsle'
xc.f:(.text+0x1bc1): undefined reference to `s_stop'
auxf95.o: In function `second_':
auxf95.f:(.text+0x8): undefined reference to `for_cpusec'
auxf95.o: In function `cal_date_':
auxf95.f:(.text+0x43): undefined reference to `for_date_and_time'
auxf95.f:(.text+0x87): undefined reference to `for_write_int_fmt'
auxf95.f:(.text+0xae): undefined reference to `for_write_int_fmt_xmit'
auxf95.f:(.text+0xe7): undefined reference to `for_write_int_fmt_xmit'
auxf95.f:(.text+0x117): undefined reference to `for_write_int_fmt_xmit'
auxf95.f:(.text+0x157): undefined reference to `for_write_int_fmt_xmit'
collect2: ld returned 1 exit status
make: *** [atm] Error 1


the top of the makefile I have reads:

#
# Makefile for ATM
# ---------------------------------------------------------------
#
.SUFFIXES: .f .o .a .prj .smb .log
#
#----------------------------------------------$$$$$
# EDIT the following lines to suit your system
#
FC= f95
FFLAGS= -O
LDFLAGS=
AUX_OBJS= auxf95.o   # Change if you do not have
#                    Â#a fortran-90 compiler
#----------------------------------------------$$$$$



Any help would be appreciated

---

