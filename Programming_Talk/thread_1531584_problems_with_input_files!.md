---
title: "problems with input files!"
date: 2010-07-15
forum: Programming Talk
---

### Post by Milenkonslisboa on 2010-07-15
I have fortran code,try to make it with f77.I get this:
milenko@hp6830s:~/eik$ make
make: Circular eik.out <- eik dependency dropped.
f77  -O1 -o eik.o 
/usr/bin/f77: No input files specified
make: *** [eik] Error 255
This is make makefile:
#
    F77=f77
    FFLAGS= -O1
# Executables
eik: eik.o  eik.out vel1 eik.para  velo 
    $(F77)  $(FFLAGS) -o eik.o 
# Object files
eik.o: eik.f eik.out vel1 eik.para  velo 
    $(F77)  $(FFLAGS) -c eik.f -o eik.o 
I don't get where is the problem.

---

### Post by trent.josephsen on 2010-07-15
This is why make echos command lines:
```
f77 -O1 -o eik.o
```
See a problem?

---

### Post by trent.josephsen on 2010-07-15
Okay, what is it with the Quick Reply feature?  Every single time I use it, it posts twice. <fume>

---

### Post by Milenkonslisboa on 2010-07-15
Thanks,but where is the problem?More details if possible.

---

### Post by PaulM1985 on 2010-07-15
I think the problem is that the line that is echoed to the command line doesn't have any input files to compile.

Paul

---

### Post by Milenkonslisboa on 2010-07-15
Code:
 open(13,file='eik.out',status='unknown')
 open(11,file='eik.para',status='unknown')
 open(21,file='velo',status='unknown')
 print* ,'enter input file name for velocity field'
       read(*, 1003) fname
1003   format(a20)
       open(12,file=fname,status='unknown')

---

### Post by Some Penguin on 2010-07-15
SPECIFY THE INPUT FILE NAME IN THE COMMAND.  Sheesh.

And in case it's still not obvious, "-o" means OUTPUT.

---

### Post by Milenkonslisboa on 2010-07-16
How should I do that?
After make -d  get this:
Must remake target `eik'.
f77  -O1 -o eik.o 
Putting child 0x00e914d0 (eik) PID 4708 on the chain.
Live child 0x00e914d0 (eik) PID 4708 
/usr/bin/f77: No input files specified
Reaping losing child 0x00e914d0 PID 4708 
make: *** [eik] Error 255
Removing child 0x00e914d0 PID 4708 from chain.

---

### Post by PaulM1985 on 2010-07-16
You will probably find a solution here:

[http://lmgtfy.com/?q=how+to+compile+fortran+code+in+linux](http://lmgtfy.com/?q=how+to+compile+fortran+code+in+linux)

Paul

---

