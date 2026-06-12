---
title: "compileing programs prob"
date: 2010-10-24
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-10-24
here my hello world work find on my gvim editor but not in netbeans 
 
#include <stdio.h> 
 
main() 
{ 
  for(;[IMG]http://forums.netbeans.org/images/smiles/icon_wink.gif[/IMG] 
      { 
          printf ("Hello World!\n"); 
      } 
} 
 
Here the error message 
 
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf 
make[1]: Entering directory `/home/perlsyntax/NetBeansProjects/CppApplication_1' 
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/cppapplication_1 
make[2]: Entering directory `/home/perlsyntax/NetBeansProjects/CppApplication_1' 
mkdir -p dist/Debug/GNU-Linux-x86 
gcc     -o dist/Debug/GNU-Linux-x86/cppapplication_1 build/Debug/GNU-Linux-x86/hello.o build/Debug/GNU-Linux-x86/main.o   
build/Debug/GNU-Linux-x86/main.o: In function `main': 
/home/perlsyntax/NetBeansProjects/CppApplication_1/main.c:14: multiple definition of `main' 
build/Debug/GNU-Linux-x86/hello.o:/home/perlsyntax/NetBeansProjects/CppApplication_1/hello.c:5: first defined here 
collect2: ld returned 1 exit status 
make[2]: *** [dist/Debug/GNU-Linux-x86/cppapplication_1] Error 1 
make[1]: *** [.build-conf] Error 2 
make: *** [.build-impl] Error 2 
make[2]: Leaving directory `/home/perlsyntax/NetBeansProjects/CppApplication_1' 
make[1]: Leaving directory `/home/perlsyntax/NetBeansProjects/CppApplication_1' 
 
BUILD FAILED (exit value 2, total time: 114ms)

---

### Post by Sub101 on 2010-10-24
Have a check what files are in: 

/home/perlsyntax/NetBeansProjects/CppApplication_1/

Or run this and post the result if your not sure;

```

cd /home/perlsyntax/NetBeansProjects/CppApplication_1/
ls
```

---

### Post by pythonsyntax on 2010-10-24
build  dist  hello.c  main.c  Makefile  nbproject

---

### Post by pythonsyntax on 2010-10-24
anyone?

---

### Post by gmargo on 2010-10-24
> **pythonsyntax said:**
> 
/home/perlsyntax/NetBeansProjects/CppApplication_1/main.c:14: **multiple definition of `main' **

The error message tells all.  You have main() defined more than once.  Probably once in main.c and once in hello.c.  Remove one of them.

---

