---
title: "Compiling Error With Module File"
date: 2009-12-06
forum: Programming Talk
---

### Post by jr226 on 2009-12-06
I am trying to compile a program in Gfortran which uses a module file.  The module is used to hold global data for the program.  When I compile I get the error:

[INDENT]C:\Program Files\gfortran\bin/ld.exe:vehpar.mod:vehpar.mod: file format not recognized; treating as linker script
C:\Program Files\gfortran\bin/ld.exe:vehpar.mod:1: syntax error
collect2: ld returned 1 exit status[/INDENT]

My 'Makefile' looks like:
[INDENT]objects = vehpar.mod vehcall.o vehmod.o tireinterp.o

Vehmod: $(objects)
	gfortran -g -o vehmod.exe $(objects)

vehpar.mod:vehpar.f90
	gfortran -g -c vehpar.f90

Vehcall.o:vehcall.f90
	gfortran -g -c vehcall.f90

vehmod.o:vehmod.f90
	gfortran -g -c vehmod.f90

tireinterp.o:tireinterp.f90
	gfortran -g -c tireinterp.f90[/INDENT]

I have tried removing all the old objects and mod file, with no sucess.  I also tried compiling the mod file outside of the makefile and just using the makefile to produce the .o files and link, but still with no success.

I am running Windows 7, and have successfully compiled code with Modules on my system before.  I also tried compiling on Kubuntu on my laptop, with no success there either.

---

### Post by jr226 on 2009-12-06
I figured it out, the compiling should not include the *.mod in the linker line, only the *.o file.  Just figured in case someone else is as dumb as I am that the sol'n should be here.  Thanks!

---

