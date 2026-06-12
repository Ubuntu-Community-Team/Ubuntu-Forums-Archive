---
title: "Is there a Fortran compiler on the system?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by duan77084 on 2008-11-24
Hi, all,

     Is there a Fortran compiler, including C, C++ and Java compiler, on the system?


      Thanks a lot in advance.

---

### Post by quimico69 on 2008-11-24
it should be in the installation CD.  try

sudo apt-get install gfortran

and install the dependencies too

---

### Post by quimico69 on 2008-11-24
sorry, it should be

sudo apt-get install gcc gfortran g++, gij

to install the C, Fortran and C++ and Java compilers, resp.  Although I don't know how good gij is.  I'd rather try the Sun stuff

---

### Post by OutOfReach on 2008-11-24
For C and C++ there is gcc which can be installed through build-essential:
```

sudo apt-get install build-essential

```
build-essential give you all the tools necessary to compile an application.
I am not sure about Java.

---

### Post by quimico69 on 2008-11-24
sorry, it should be

sudo apt-get install gcc gfortran g++ gij

to install the C, Fortran and C++ and Java compilers, resp.  Although I don't know how good gij is.  I'd rather try the Sun stuff

---

