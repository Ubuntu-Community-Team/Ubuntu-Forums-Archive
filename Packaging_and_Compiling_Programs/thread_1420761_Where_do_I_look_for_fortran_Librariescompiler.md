---
title: "Where do I look for fortran Libraries/compiler?"
date: 2010-03-03
forum: Packaging and Compiling Programs
---

### Post by epi 1:10,000 on 2010-03-03
I have an old Biochemistry Structural analysis program that I would like to run but it is old and written in Fortran.  Does anyone know where to find the appropriate libraries/compiler so I can compile it?

---

### Post by diesch on 2010-03-03
Ubuntu comes with GNU Fortran (package gfortran) and some fortran libs. Search in Synaptic for fortran.

---

### Post by epi 1:10,000 on 2010-03-03
I tried gFortran which is fortran 95 but my program was written in fortran 77.   I get syntax errors in gfortran, can anyone suggest a good debuger?  I guess I'm gona have to learn fortran.  Some one else recommend an IBM compiler which cost $5,000 but its not worth that much to me.

---

### Post by diesch on 2010-03-03
*f2c* translates Fortran 77 into C, *fort77* is a frontend for f2c that lets you use *f2c* like a real compiler

---

