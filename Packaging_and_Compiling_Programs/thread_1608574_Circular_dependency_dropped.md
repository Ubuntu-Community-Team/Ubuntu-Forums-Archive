---
title: "Circular dependency dropped"
date: 2010-10-29
forum: Packaging and Compiling Programs
---

### Post by Nikolazigic on 2010-10-29
I have a problem:trying to compile one program,changed it slightly but I get this:
make: Circular findiff2d <- findiff2d.o dependency dropped.
findiff2d calls 9 subroutines some of them are called from main program too.Is that problem?
This is my makefile:
77 = ifort
    LD = ifort
    CPPFLAGS = -C -traditional $(DFLAGS) -I$(INTEL_INC)
    FCFLAGS = $(DFLAGS) -I$(INTEL_INC) -fpp -g 
    LDFLAGS = $(FCFLAGS)
    LIBS = -L$(INTEL_LIB) -lmkl_intel_lp64
    OBJECTS_ARCHITECTURE = machine_intel.o

    
# Executables
main:  main.o model.o time.o findiff2d.o misc.o blkdat.o  fd.par fd.com
    $(F77) $(FLAGS) -o main main.o model.o time.o findiff2d.o misc.o blkdat.o

# Object files
main.o: main.f fd.par fd.com
    $(F77)  $(FLAGS) -c main.f -o main.o
model.o: model.f fd.par fd.com
    $(F77)   $(FLAGS) -c model.f -o model.o
time.o: time.f fd.par fd.com
    $(F77)  $(FLAGS) -c time.f -o time.o
findiff2d.o: findiff2d fd.par fd.com
    $(F77)  $(FLAGS) -c findiff2d.f -o findiff2d.o
misc.o: misc.f fd.par fd.com
    $(F77)  $(FLAGS) -c misc.f -o misc.o
blkdat.o: blkdat.f fd.par fd.com
    $(F77)  $(FLAGS) -c blkdat.f -o blkdat.o

---

### Post by gmargo on 2010-10-30
> **Nikolazigic said:**
> ```

findiff2d.o: findiff2d fd.par fd.com

```

That should be 
```

findiff2d.o: findiff2d.f fd.par fd.com

```Note the **.f** suffix on the first dependency.

---

