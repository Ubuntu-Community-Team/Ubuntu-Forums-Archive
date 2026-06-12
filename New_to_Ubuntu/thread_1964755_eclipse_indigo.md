---
title: "eclipse indigo"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by etigho on 2012-04-24
hi every one
I want to run this makefile and watch the current line of execution in highlight mode. is  anybody sure that if I install eclipse indigo, it’ll work? I also appreciate any suggestion for other debuggers too.
Thanks in advanced.

SPATIALDIM=2

F77 = f95
#F77 = g77
cc  = cc
CC  = CC
FOPTF = 
FFLAGS = 
CCFLAGS = 
#FORTLIBS = -lF77 -Bdynamic -lV77 -lc 
cLIBS = -lm

PRECISION = -DUSE_DOUBLE
OPSYS = -DUNIX -DSUN

# machine dependent macro defs
CDEF  = $(OPSYS) $(PRECISION)

# problem dependent dependencies


.SUFFIXES:

.SUFFIXES: .C .o .F .f .c .cc .cpp

hSRC  = eno.h fluids.h eno.xtn fluids.xtn

fSRC  = heavy.f xaverage.f yaverage.f

cSRC  = eno.c conserve.c elliptic.c eno_conf.c eno_init.c \
        fdiff.c fluids.c invert.c reset1.c stream.c tension.c \
        brute_reset.c postproc.c mgrid.c stokes.c

OBJS =  $(cSRC:.c=.o) $(fSRC:.f=.o) 

# main target
enon:    $(OBJS) 
	$(F77) -v  $(CCFLAGS) $(OBJS) -o enon

# stub targets

.c.o:
	cc -c $(CDEF) $*.c

.f.o:
	$(F77) -c $(FFLAGS) $*.f

---

