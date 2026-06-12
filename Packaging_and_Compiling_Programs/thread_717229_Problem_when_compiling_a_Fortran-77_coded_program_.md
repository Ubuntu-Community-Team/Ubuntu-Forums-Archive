---
title: "Problem when compiling a Fortran-77 coded program (ISAAC)"
date: 2008-03-06
forum: Packaging and Compiling Programs
---

### Post by Senza on 2008-03-06
I've been looking around the threads relating to Fortran on this forum and the rest of the net but can't seem to figure it out. I'm trying to compiler a CFD program called ISAAC - [http://isaac-cfd.sourceforge.net/](http://isaac-cfd.sourceforge.net/) . I've installed g77 and it's dependents and even installed the Intel Fortran compiler. I've installed build-essential also. I've extracted the source files and makefiles into /src folder. When i attempt to use Intel Fortran i get this error (although i haven't messed about with it much):

```
peter@arcturus:~/ISAAC/src$ ifort make
/home/peter/IntelFortran/lib/for_main.o: In function `main':
/users/nbtester/x86linux_nightly/branch-10_1/20080112_010000/libdev/frtl/src/libfor/for_main.c:(.text+0x39): undefined reference to `MAIN__'
```

When i use g77 (by just typing 'make' in the source directory), i get these errors:

```
peter@arcturus:~/ISAAC/src$ make
cd /home/peter/ISAAC/src/main;\
        make -f main.mk "HOME=/home/peter" "SRC=/home/peter/ISAAC/src" "FFLAGS=-O2" \
                "FC=f77" "CPPFLAGS=-DCPU_TIME";\
        ln *.o /home/peter/ISAAC/src
make[1]: Entering directory `/home/peter/ISAAC/src/main'
f77 -O2 -DCPU_TIME  -c -o main.o main.F
main.F: In program `isaac':
main.F:198: 
         include '../header/common.h'
         ^
Unable to open INCLUDE file `../header/common.h' at (^)
main.F:199: 
         include '../header/histry.h'
         ^
Unable to open INCLUDE file `../header/histry.h' at (^)
main.F:457: 
         IFCHAR(IFROE,1) = IFDS
         ^
Invalid form for IF statement at (^)
main.F:614: 
               IF (THREED) THEN
                   ^
Expression at (^) has incorrect data type or rank for its context
main.F:777: 
         IF (FOURTH) THEN
             ^
Expression at (^) has incorrect data type or rank for its context
main.F:808: 
               IF (THREED) THEN
                   ^
Expression at (^) has incorrect data type or rank for its context
main.F:867: 
         IF (FOURTH) THEN
             ^
Expression at (^) has incorrect data type or rank for its context
main.F:1034: 
               IF (IFWALF) THEN
                   ^
Type disagreement between expressions at (^) and (^)
main.F:1245: 
                     IF (INITTD) THEN
                         ^
Type disagreement between expressions at (^) and (^)
main.F:2065: 
                                    MUTALG = .TRUE.
                                    1        2
Type disagreement between expressions at (1) and (2)
main.F:2067: 
                                    MUTALG = .FALSE.
                                    1        2
Type disagreement between expressions at (1) and (2)
main.F:2271: 
                                 R2(IT) = R2NORM(NF+1)
                                 ^
Invalid declaration of or reference to symbol `r2' at (^) [initially seen at (^)]
main.F:2328: warning:
                                    IF (NRELIZ( 9) .GT. 0) THEN
                                                ^
Array element value at (^) out of defined range
main.F:2329: warning:
                                       WRITE (IOUT,2420) 'XY', NRELIZ( 9)
                                                                       ^
Array element value at (^) out of defined range
main.F:2332: warning:
                                    IF (NRELIZ(10) .GT. 0) THEN
                                               ^
Array element value at (^) out of defined range
main.F:2333: warning:
                                       WRITE (IOUT,2420) 'XZ', NRELIZ(10)
                                                                      ^
Array element value at (^) out of defined range
main.F:2336: warning:
                                    IF (NRELIZ(11) .GT. 0) THEN
                                               ^
Array element value at (^) out of defined range
main.F:2337: warning:
                                       WRITE (IOUT,2420) 'YZ', NRELIZ(11)
                                                                      ^
Array element value at (^) out of defined range
main.F:2637: 
               IF ( THREED ) THEN
                    ^
Expression at (^) has incorrect data type or rank for its context
main.F:2648: 
               IF ( THREED ) THEN
                    ^
Expression at (^) has incorrect data type or rank for its context
main.F:2661: 
                  IF ( THREED ) THEN
                       ^
Expression at (^) has incorrect data type or rank for its context
main.F:2677: 
               IF ( THREED ) THEN
                    ^
Expression at (^) has incorrect data type or rank for its context
main.F:2690: 
               IF ( THREED ) THEN
                    ^
Expression at (^) has incorrect data type or rank for its context
main.F:2705: 
                  IF ( THREED ) THEN
                       ^
Expression at (^) has incorrect data type or rank for its context
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/peter/ISAAC/src/main'
ln: accessing `*.o': No such file or directory
make: *** [all] Error 1

```

'make' seems to be doing more, and is the method recommended in the documentation. also, i've just installed Ubuntu 7.10 tonight, so it's a fresh install although i've been using SUSE at uni for a couple of weeks but need to do calculations with this program at home.

Any ideas at all?

---

### Post by geraldm on 2008-03-09
The first errors to correct are header files.  Look into how to pass the include directories to the compiler.  Perhaps -I {dir} ?

Gerald

---

### Post by WW on 2008-03-09
I'm on a Mac right now, and I don't know if this would be any different using Ubuntu, but here's what I just did.

The only Fortran compiler that I have installed is gfortran, but it can compile Fortran-77.

I downloaded and extracted the files isaacsrc.4_2.tar.gz and isaacmk.4_2.tar.gz.

In the directory where I extracted the files, I used **make** with FC redefined:
> 
$ make FC=gfortran

I got a few warnings in main.F about array references being out of bounds, but the build finished.

---

