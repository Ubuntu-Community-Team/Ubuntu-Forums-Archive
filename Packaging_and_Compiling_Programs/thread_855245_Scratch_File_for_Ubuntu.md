---
title: "Scratch File for Ubuntu"
date: 2008-07-10
forum: Packaging and Compiling Programs
---

### Post by Dahaka14 on 2008-07-10
Hello, I'm trying to run my professor's programs in FORTRAN 77 code on Hardy Ubuntu.  He gave me the source code, and everything went well in compiling using the "f77" command, but then I got this:

non.f: In program `MAIN__':
non.f:211: 
         OPEN(UNIT=ISC1,FILE='SCR1.DAT',STATUS='SCRATCH')
                        1               2
Conflicting I/O control specifications at (1) and (2)
non.f:212: 
         OPEN(UNIT=ISC2,FILE='SCR2.DAT',STATUS='SCRATCH')
                        1               2
Conflicting I/O control specifications at (1) and (2)
non.f:213: 
         OPEN(UNIT=ISC3,FILE='SCR3.DAT',STATUS='SCRATCH')
                        1               2
Conflicting I/O control specifications at (1) and (2)

and then it went back to the command line.  My professor says I need to find out how to write a scratch file for my computer.  Can someone please help me fix this problem?

UPDATE:
Here are lines 210-213:

OPEN(UNIT=IOUT, FILE='FGR.LST',STATUS='NEW')
      OPEN(UNIT=ISC1,FILE='SCR1.DAT',STATUS='SCRATCH')
      OPEN(UNIT=ISC2,FILE='SCR2.DAT',STATUS='SCRATCH')
      OPEN(UNIT=ISC3,FILE='SCR3.DAT',STATUS='SCRATCH')

---

