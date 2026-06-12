---
title: "Netbeans C++ compile error"
date: 2010-03-29
forum: Programming Talk
---

### Post by abraxas334 on 2010-03-29
I am using netbeans as an ide. After finally getting a linear algebra library working (commandline) I would like to use netbeans for development.
When I am in the project folder I can get the test program compiled and running fine using commandline no problem. It looks like this:

```
g++ main.cpp -o my_lsymreg -I ../../workspace/arpack++/arpack++/examples/matrices/sym -I ../../workspace/arpack++/arpack++/include -lsuperlu -larpack -llapack -lblas -lgfortran -lgfortranbegin -lnsl
```

In netbeans however I get an error:

```
g++ -lsuperlu -larpack -llapack -lblas -lgfortran -lgfortranbegin -lnsl    -o dist/Debug/GNU-Linux-x86/tnttest build/Debug/GNU-Linux-x86/main.o
build/Debug/GNU-Linux-x86/main.o: In function `main':
/home/antonia/NetBeansProjects/tntTest/main.cpp:48: multiple definition of `main'
/usr/lib/gcc/i486-linux-gnu/4.3.3/libgfortranbegin.a(fmain.o):(.text+0x0): first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/libgfortranbegin.a(fmain.o): In function `main':
```

My netbeans is set up like this: 
under project properties and the C++compiler tab I have the under the include Directories section the two include directories and for the command line the additional options all the -.... bits.

Any ideas?

---

### Post by dwhitney67 on 2010-03-29
You have two main() functions defined... one in main.cpp, the other in the libgfortranbegin.a static library, specifically in the "fmain" module.

If it is needed, consider renaming the function that is in the library.

---

### Post by abraxas334 on 2010-03-29
> You have two main() functions defined... one in main.cpp, the other in the libgfortranbegin.a static library, specifically in the "fmain" module.


Yes I understand that, but what I don't understand is that if i compile using a terminal, I don't get that same error and it compiles and runs fine. Only when I use the "compile" button in the netbeans ide!
I definitely don't want to mess with the static library because I don't know what it does exactly.

---

### Post by dwhitney67 on 2010-03-29
> **abraxas334 said:**
> Yes I understand that, but what I don't understand is that if i compile using a terminal, I don't get that same error and it compiles and runs fine. Only when I use the "compile" button in the netbeans ide!
I definitely don't want to mess with the static library because I don't know what it does exactly.

Through a little experimentation, I found that I could duplicate the issue you are having via the command line.  If one specifies their library *before* their main.o file, in the final linking stage, then the error pops up.

Thus, from your earlier post, this statement is causing your linking woes:
```

g++ -lsuperlu -larpack -llapack -lblas -lgfortran -lgfortranbegin -lnsl    -o dist/Debug/GNU-Linux-x86/tnttest build/Debug/GNU-Linux-x86/main.o

```

See if you can get Netbeans to specify your main.o file before linking with any libraries.  For example:
```

g++ build/Debug/GNU-Linux-x86/main.o -lsuperlu -larpack -llapack -lblas -lgfortran -lgfortranbegin -lnsl -o dist/Debug/GNU-Linux-x86/tnttest

```


P.S.  Have you considered that perhaps you do not need a main() function?  What does the library's main() function do/serve?

---

