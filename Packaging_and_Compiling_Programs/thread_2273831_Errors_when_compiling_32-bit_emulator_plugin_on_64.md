---
title: "Errors when compiling 32-bit emulator plugin on 64-bit system"
date: 2015-04-16
forum: Packaging and Compiling Programs
---

### Post by Zeikcied on 2015-04-16
I'm having difficulty compiling a sound plugin for a PlayStation emulator.  The emulator in question is ePSXe, which is 32-bit, so I have to compile the plugin as 32-bit on my 64-bit Kubuntu 14.10 system.

The plugin is the P.E.Op.S. Sound Plugin 1.9.  The source code is found here: [http://sourceforge.net/projects/peops/files/peopsspu/P.E.Op.S.%20Sound%20SPU%201.9/](http://sourceforge.net/projects/peops/files/peopsspu/P.E.Op.S.%20Sound%20SPU%201.9/)

I want to compile it in ALSA mode, which is handled by a simple flag.  Here's the make file:

```
##############################################################################
# MAKEFILE FOR THE PEOPS OSS SPU... just run "make"
##############################################################################

##############################################################################
# 1. SETS (CCFLAGS3 is used)
##############################################################################

# Set to TRUE to build the ALSA support
USEALSA = FALSE
# Set to TRUE to disable the thread library support - helpful for some Linux distros
NOTHREADLIB = FALSE

##############################################################################

CC = gcc
CCFLAGS1 = -fPIC -c -Wall -m486 -O3
CCFLAGS2 = -fPIC -c -Wall -m486 -O2 -ffast-math
CCFLAGS3 = -fPIC -c -Wall -mpentium -O3 -ffast-math -fomit-frame-pointer
INCLUDE =
LINK = gcc
OBJ =   spu.o cfg.o dma.o freeze.o psemu.o registers.o zn.o
LIB = -lc -lm -L/usr/X11R6/lib -L/usr/lib

ifeq ($(USEALSA), TRUE)
	OBJ+= alsa.o
	LIB+= -lasound
	LINKFLAGS = -shared -Wl,-soname,libspuPeopsALSA.so -o libspuPeopsALSA.so.1.0.9
	CCFLAGS3+= -DUSEALSA
else
	OBJ+= oss.o
	LINKFLAGS = -shared -Wl,-soname,libspuPeopsOSS.so -o libspuPeopsOSS.so.1.0.9
endif

ifeq ($(NOTHREADLIB), TRUE)
	CCFLAGS3+= -DNOTHREADLIB
else
	LIB+= -lpthread
endif



##############################################################################
# 2. MAIN RULE
##############################################################################

spuPeopsOSS :	$(OBJ)
		$(LINK) $(LINKFLAGS) $(OBJ) $(LIB)

##############################################################################
# 3. GENERAL RULES
##############################################################################

%.o     : %.c
	$(CC) $(CCFLAGS3) $(INCLUDE) $<

##############################################################################
# 4. SPECIFIC RULES
##############################################################################

spu.o  : spu.c stdafx.h externals.h cfg.h dsoundoss.h regs.h debug.h xa.c reverb.c adsr.c
cfg.o  : cfg.c stdafx.h externals.h
dma.o : dma.c stdafx.h externals.h
freeze.o : freeze.c stdafx.h externals.h registers.h spu.h regs.h
oss.o : oss.c stdafx.h externals.h
alsa.o : alsa.h stdafx.h externals.h
psemu.o : psemu.c stdafx.h externals.h regs.h dma.h
registers.o : registers.c stdafx.h externals.h registers.h regs.h reverb.h
zn.o : zn.c stdafx.h xa.h

.PHONY: clean spuPeopsOSS

clean:
	rm -f *.o *.so

```

So I set USEALSA to TRUE to set it to use ALSA.  I have to remove -mpentium, because that's not recognized by GCC anymore, as best as I can tell.  Running make with that set has GCC say it's unrecognized.  If I change it to -m32 and run make, however, I get these errors:

```
/usr/bin/ld: i386 architecture of input file `spu.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `cfg.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `dma.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `freeze.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `psemu.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `registers.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `zn.o' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `alsa.o' is incompatible with i386:x86-64 output
/usr/bin/ld: spu.o: file class ELFCLASS32 incompatible with ELFCLASS64
/usr/bin/ld: final link failed: File in wrong format
collect2: error: ld returned 1 exit status
Makefile:48: recipe for target 'spuPeopsOSS' failed
make: *** [spuPeopsOSS] Error 1
```

I don't know enough about compiling and whatnot to understand what the problem is.  Can someone help me figure this out?

---

### Post by steeldriver on 2015-04-16
Did you make previous 'make' attempts before adding the -m32 flag? if so, you could have 64-bit object (.o) files left over that make considers to be up-to-date and hence isn't attempting to rebuild - remove all .o files from the directory and try again

---

### Post by Zeikcied on 2015-04-16
> **steeldriver said:**
> Did you make previous 'make' attempts before adding the -m32 flag? if so, you could have 64-bit object (.o) files left over that make considers to be up-to-date and hence isn't attempting to rebuild - remove all .o files from the directory and try again

No, I'm starting with a fresh src directory each time I run make.  So there shouldn't be any 64-bit .o files in there.

---

### Post by steeldriver on 2015-04-16
I think you probably need to add the -m32 flag to the link phase as well as the compile phase - either by modifying the LINKFLAGS or by changing the LINK variable itself e.g.

```

LINK = gcc -m32

```

---

### Post by Zeikcied on 2015-04-16
> **steeldriver said:**
> I think you probably need to add the -m32 flag to the link phase as well as the compile phase - either by modifying the LINKFLAGS or by changing the LINK variable itself e.g.

```

LINK = gcc -m32

```

Okay, I did what you suggested, and it got rid of those errors, but I have a new one.

```
/usr/bin/ld: cannot find -lasound
collect2: error: ld returned 1 exit status
Makefile:48: recipe for target 'spuPeopsOSS' failed
make: *** [spuPeopsOSS] Error 1
```

---

