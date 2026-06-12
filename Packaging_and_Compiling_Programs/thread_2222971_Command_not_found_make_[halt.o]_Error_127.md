---
title: "Command not found make: ***[halt.o] Error 127"
date: 2014-05-08
forum: Packaging and Compiling Programs
---

### Post by Brcara on 2014-05-08
[EMAIL="csc288@csc288-laptop:~/Desktop/csc112_256/as4/nachos-3.4.linux"]csc288@csc288-laptop:~/Desktop/csc112_256/as4/nachos-3.4.linux[/EMAIL]-LAB4/code/test$ make


/shared/Alice//cross/mips-unknown-elf/bin/gcc -G 0 -c -I../userprog -I../threads -c -S halt.c
make: /shared/Alice//cross/mips-unknown-elf/bin/gcc: Command not found
make: *** [halt.o] Error 127

This error appears as a part of making NachOS. 
Here is the make file currently:
```
# use normal make for this Makefile
#
# Makefile for building user programs to run on top of Nachos
#
# Several things to be aware of:
#
#    Nachos assumes that the location of the program startup routine (the
#     location the kernel jumps to when the program initially starts up)
#       is at location 0.  This means: start.o must be the first .o passed 
#     to ld, in order for the routine "Start" to be loaded at location 0
#


# if you are cross-compiling, you need to point to the right executables
# and change the flags to ld and the build procedure for as
# GCCDIR = ~/gnu/local/decstation-ultrix/bin/
 GCCDIR = /shared/Alice//cross/mips-unknown-elf/bin/
 LDDIR= /shared/Alice/cross/decstation-ultrix/bin/
 LDFLAGS = -T script -N
# LDFLAGS = -N -T 0
# LDFLAGS = 
 ASFLAGS = -mips
 ASFLAGS = 
 CPPFLAGS = $(INCDIR)




# if you aren't cross-compiling:
# GCCDIR =
# LDFLAGS = -N -T 0
# ASFLAGS =
# CPPFLAGS = -P $(INCDIR)




CC = $(GCCDIR)gcc
AS = $(LDDIR)as
LD = $(LDDIR)ld


CPP = /usr/bin/cpp
INCDIR =-I../userprog -I../threads
CFLAGS = -G 0 -c $(INCDIR)


all: halt shell matmult sort test1


start.o: start.s ../userprog/syscall.h
    $(CPP) $(CPPFLAGS) start.s > strt.s
    $(AS) $(ASFLAGS) -o start.o strt.s
    rm strt.s


halt.o: halt.c
    $(CC) $(CFLAGS) -c -S halt.c
    $(AS) $(ASFLAGS) -o halt.o halt.s


halt: halt.o start.o
    $(LD) $(LDFLAGS) start.o halt.o -o halt.coff
    ../bin/coff2noff halt.coff halt


shell.o: shell.c
    $(CC) $(CFLAGS) -c -S shell.c
    $(AS) $(ASFLAGS) -o shell.o shell.s


shell: shell.o start.o
    $(LD) $(LDFLAGS) start.o shell.o -o shell.coff
    ../bin/coff2noff shell.coff shell


sort.o: sort.c
    $(CC) $(CFLAGS) -c -S sort.c
    $(AS) $(ASFLAGS) -o sort.o sort.s


sort: sort.o start.o
    $(LD) $(LDFLAGS) start.o sort.o -o sort.coff
    ../bin/coff2noff sort.coff sort


matmult.o: matmult.c
    $(CC) $(CFLAGS) -c -S matmult.c
    $(AS) $(ASFLAGS) -o matmult.o matmult.s


matmult: matmult.o start.o
    $(LD) $(LDFLAGS) start.o matmult.o -o matmult.coff
    ../bin/coff2noff matmult.coff matmult


test1.o: test1.c
    $(CC) $(CFLAGS) -c -S test1.c
    $(AS) $(ASFLAGS) -o test1.o test1.s


test1: test1.o start.o
    $(LD) $(LDFLAGS) start.o test1.o -o test1.coff
    ../bin/coff2noff test1.coff test1


```

---

### Post by oldos2er on 2014-05-09
Moved to Packaging & Compiling Programs.

---

