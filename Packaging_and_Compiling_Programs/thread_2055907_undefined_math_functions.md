---
title: "undefined math functions"
date: 2012-09-10
forum: Packaging and Compiling Programs
---

### Post by regibb on 2012-09-10
CXX = gcc
CCFLAGS = -g -Wall
LIB = /home/regibb/lib/lbse1
OBJS = xbsstep.o
LIBOBJS = bsstep.o rzextr.o pzextr.o odeint.o mmid.o free_vector.o nrerror.o vector.o matrix.o free_matrix.o

.c.o :
    ${CXX} ${CCFLAGS} -c $<
orbitale1 : ${OBJS} ${LIB}
    ${CXX} ${CCFLAGS} -o $@ ${OBJS} ${LIB}
lbse1 : ${LIBOBJS}
    ar r ${LIB} $?
============================================================================
regibb@ubuntu:~/source/ode/orbitale1$ make orbitale1
gcc -g -Wall -o orbitale1 xbsstep.o /home/regibb/lib/lbse1
xbsstep.o: In function `drag':
/home/regibb/source/ode/orbitale1/xbsstep.c:29: undefined reference to `exp'
xbsstep.o: In function `main':
/home/regibb/source/ode/orbitale1/xbsstep.c:97: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:112: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:113: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:114: undefined reference to `cos'
/home/regibb/source/ode/orbitale1/xbsstep.c:116: undefined reference to `sin'
/home/regibb/source/ode/orbitale1/xbsstep.c:117: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:122: undefined reference to `sqrt'
/home/regibb/source/ode/orbitale1/xbsstep.c:125: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:126: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:127: undefined reference to `cos'
/home/regibb/source/ode/orbitale1/xbsstep.c:128: undefined reference to `sin'
/home/regibb/source/ode/orbitale1/xbsstep.c:129: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:129: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:129: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:129: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/xbsstep.c:129: undefined reference to `pow'
xbsstep.o:/home/regibb/source/ode/orbitale1/xbsstep.c:130: more undefined references to `pow' follow
xbsstep.o: In function `main':
/home/regibb/source/ode/orbitale1/xbsstep.c:135: undefined reference to `sqrt'
/home/regibb/source/ode/orbitale1/xbsstep.c:136: undefined reference to `fmod'
/home/regibb/source/ode/orbitale1/xbsstep.c:141: undefined reference to `sqrt'
/home/regibb/lib/lbse1(bsstep.o): In function `bsstep':
/home/regibb/source/ode/orbitale1/bsstep.c:64: undefined reference to `pow'
/home/regibb/source/ode/orbitale1/bsstep.c:91: undefined reference to `pow'
collect2: ld returned 1 exit status

---

### Post by Zill on 2012-09-10
regibb:  Is there actually a question here?  I think some more information is required.  Please read the following link...
[LIST]
[*][Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showpost.php?p=8920811&postcount=1")
[/LIST]

---

### Post by steeldriver on 2012-09-10
in the absence of any other information the obvious suggestion would be to add the math library directive '-lm' either to your LIB variable or on the linker command line

---

### Post by regibb on 2012-09-10
i have been able to compile this same program on a 32 bit system that also had ubnuntu 12.04.  i will state the obvious...i am a duck out of water:  i have never used this forum or
any forum before.  a regular green horn.  when i try to compile orbitale1 i get all those undefined messages for math functions on this newer 64 bit system, but not on my older 32 bit system.   now, did use c++ on the 32 bit system

---

### Post by oldos2er on 2012-09-10
Moved to Packaging and Compiling Programs.

---

### Post by regibb on 2012-09-10
CXX = gcc
CCFLAGS = -g -Wall
LIB = /home/regibb/lib/lbse1 -lm
OBJS = xbsstep.o
LIBOBJS = bsstep.o rzextr.o pzextr.o odeint.o mmid.o free_vector.o nrerror.o vector.o matrix.o free_matrix.o

.c.o :
    ${CXX} ${CCFLAGS} -c $<
orbitale1 : ${OBJS} ${LIB}
    ${CXX} ${CCFLAGS} -o $@ ${OBJS} ${LIB}
lbse1 : ${LIBOBJS}
    ar r ${LIB} $?

i added -lm to the end of the LIB variable and it is now ok!!!

---

### Post by regibb on 2012-09-10
....as far as i am concerned this post is closed.

---

### Post by Zill on 2012-09-10
> **regibb said:**
> ....as far as i am concerned this post is closed.
I am pleased that you have resolved the problem.

Would you now please "Mark this thread as solved" from the "Thread Tools" menu at the top right of the thread.  Note that only you, as the original poster, can do this.

---

