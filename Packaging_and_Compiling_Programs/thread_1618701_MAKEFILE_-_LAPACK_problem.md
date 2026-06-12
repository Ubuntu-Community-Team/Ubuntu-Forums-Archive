---
title: "MAKEFILE - LAPACK problem"
date: 2010-11-10
forum: Packaging and Compiling Programs
---

### Post by harishankerg on 2010-11-10
Hi, 

I have a problem with installing a project with Lapack. 

I am able to compile all my .f (f77) files using f77. The source codes have few LAPACK libraries. Though I have included LAPACK archive when I create my archive, I still get an error

eltype.f:365: undefined reference to `dgesv'


This is how my Makefile is

prod : $(EXEC_NAME)

all : prod
clean :
        rm -f *.o *.mod $(EXEC_NAME)
$(EXEC_NAME) : $(OBJSMOD) $(OBJS_PROD) $(OBJS)
        $(F) -o $(EXEC_NAME) $(wildcard *.a)  $(wildcard *.o) $(LDFLAGS)
%.o: %.f
        $(F) -c -g  $?

I have the LAPACK archive in the current folder. 

Eagerly waiting for suggestions. 

Thanks 
Hari

---

