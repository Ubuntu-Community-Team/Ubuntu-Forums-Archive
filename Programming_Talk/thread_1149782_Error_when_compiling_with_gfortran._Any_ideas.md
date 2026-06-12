---
title: "Error when compiling with gfortran. Any ideas ?"
date: 2009-05-05
forum: Programming Talk
---

### Post by nspattak on 2009-05-05
Hallo.

I am trying to compile a fortran code I was given using gfortran. When linking all the object files together I get thousands or millions of warning like: 
```

AIRSEA.o:1.1:

\x7FELF\x02\x01\x01\x01>\x01h\x03@@
 1
Error: Invalid character in name at (1)
AIRSEA.o:3:

AWI\x89\xCFAVAUATUSE\x8B E\x8B)E9\xEC\x0F\x8Ft\x01Ic\xC4\xF3D\x0F\x10\x05\xF3\x0F\x10=L\x8Dp\xFF\xF3\x0F\x105E\x89\xE0J\x8D\x04\xB5\xF3\x0F\x10-E\x0F(\xC8H\x8D,\x06H\x8D\x1C\x02L\x8D\x0C\x07H\x89\xDEH\x89\xEF
1
Error: Unclassifiable statement at (1)
AIRSEA.o:3.132:

E\x0F(\xC8H\x8D,\x06H\x8D\x1C\x02L\x8D\x0C\x07H\x89\xDEH\x89\xEF\xE9\xC0f\x0F\x1FD\xB9c\xBAdA\x0F(\xC8\xF3A\x0F\x10\x11\x0F(\xD8\xF3\x0F\\xD9\x0F(\xE5\xF3\x0F^\xD6\xF3\x0F\\xE3\xF3\x0F,\xC2\x83\xF8b\x0F\x8E\xBEA\xBA\x0F'A\xBB
                                                                           1                                                         
Warning: Line truncated at (1)

```

It does not make sense to me as the object files are all created by gfortran itself.

I tried the standard 9.04 compiler (4.3.3) and an experimental 4.5 I built myself some weeks ago.
Any ideas ?

---

### Post by leandromartinez98 on 2009-05-05
You should probably post the commands you are using exactly, and,
if possible, the code you are trying to compile, so people can help
you better.

---

### Post by nspattak on 2009-05-05
I am afraid this is not possible. I will try to describe it as much as I can. Anyone interested, please ask for further information. All the constants are declared in one file (wamodwk.f90) in one module. There are several other modules in another file (variables.f90) which are global variables used by several other functions/routines. There are around 90 files in total. Each is compiled using this command:
```

gfortran -Dassimilation -Dlinux -Dcoarseonly -I./ -x f95-cpp-input -O2 -mtune=native  -c $FILENAME.f90

```

then there is linking:

```

gfortran   -x f95-cpp-input -O2 -mtune=native  -o wamodwk AIRSEA.o ANALYSE.o ASSIM.o BOUINPT.o CFLSUB.o CHIEF.o cmpqb.o CORRECT.o CREWFN.o DIFDATE.o DOTDC.o F4SPEC.o FDUR.o FEMEAN.o FILLBL.o FUSTAR.o FWSEA.o GETDATA.o GETWND.o GRADI.o GSFILE.o HEADBC.o IECF_len.o IMPLSCH.o INCDATE.o INITMDL.o INTPOL.o INTSPEC.o isamax.o LOCINT.o MAKEBLO.o MAKEGRID.o NOTIM.o OIFIELD.o OPENFIL.o OPEN_SCRATCH_FILE.o OP_FILES.o OUTBC.o OUTBS.o OUTGRID.o OUTINT.o OUTPP.o OUTSPEC.o OUTSPP.o PEAKFR.o PREWIND.o PROPAGS2.o PROPDOT.o PRSPP.o PRSPPS.o READBOU.o READPRE.o READSAT.o READWND.o ROTSPEC.o sasum.o saxpy.o SBOTTOM.o SDISSIP.o sdot.o SEMEAN.o SEPWISW.o SETICE.o SFBRK.o sgeco.o sgedi.o sgefa.o SINPUT.o SNONLIN.o SPLITBL.o SPR.o sscal.o sswap.o STHQ.o STRESSO.o STRSPEC.o SYMINV.o TIMIN.o TRANS_GRID.o UPDATE.o UPWSPEC.o USERIN.o WAMODEL.o WAMWND.o WAVEMDL.o WSMFEN.o  wamodwk.o variables.o

```

which fails as soon as it starts with lots and lots of lines like the ones I posted. The code compiles and run correctly using ifort, so I guess that there is not something terribly wrong with it. I guess it also is not a gfortran issue, so I am looking for ideas. I was not able to find any information (at all...) by googling for the errors I got.

All i was able to find, is that the -x f95-cpp-input option is not documented in gfortran's man page but it is needed if one wants to compile an f90 code containing preprocessor directives. This would not be necassary if the source files were .F90 instead of .f90. I found that because in the beggining I could not even create the object files. But now I am stack and I can not accept that the gnu fortran compiler can not do at all sth that ifort can do.

---

### Post by hongo on 2010-07-01
I have the same problem. I think it is related with the line length  that is over 131 chars but I couldn't solve it yet.

---

### Post by rollett on 2011-03-24
Thank you for posting this exchange.  I discovered that using the compiler directive "-xf95-cpp-input"  causes gfortran to treat ALL files as being in need of pre-processsing, including object files.  So, the answer is to pre-compile all source files to object files, but, when linking everything together, leave out the preprocessing directive.
regards
ADR

---

