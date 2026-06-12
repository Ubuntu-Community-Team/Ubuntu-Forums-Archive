---
title: "cannot find c++ and fortran compiler"
date: 2009-05-11
forum: Packaging and Compiling Programs
---

### Post by shababhsiddique on 2009-05-11
Hello 
I am a newbie. I installed Netbeans IDE 6.5 multi language. But I cannot compile any c++ code. 

It prompts for -"resolve missing native build tools" and show directories of C,C++ and fortran compiler where c++ field is blank 

* See attachment -- Joeb454

please help me out

---

### Post by Hellfiretorch on 2009-05-16
please make sure you installed c++/gfortran compiler pack.

sudo apt-get install build-essential <- will install gnu c++ compiler pack
sudo apt-get install gfortan

---

### Post by jsmidt on 2009-05-18
First install g++ and gfortran since they are the compilers.

Then for the C++ compiler field in your screenshot put
```
/usr/bin/g++
```

For the Fortran compiler field put
```
/usr/bin/gfortran
```

Please let me know if this is confusing or doesn't work.  Good luck.

---

### Post by shababhsiddique on 2009-11-14
> **jsmidt said:**
> First install g++ and gfortran since they are the compilers.

Then for the C++ compiler field in your screenshot put
```
/usr/bin/g++
```For the Fortran compiler field put
```
/usr/bin/gfortran
```Please let me know if this is confusing or doesn't work.  Good luck.

Sorry to be late I was busy with my study. 
Thanks it worked for 8.04 havent tried with 9.10 though

---

