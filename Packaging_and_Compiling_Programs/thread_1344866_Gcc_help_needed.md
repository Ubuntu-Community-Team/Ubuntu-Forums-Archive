---
title: "Gcc help needed"
date: 2009-12-03
forum: Packaging and Compiling Programs
---

### Post by diegoallen on 2009-12-03
Im trying to compile Objective-C code using gcc, but when I use the -lobjc flag I get this output "ld: library not found for -lobjc".Ive got gobjc-4.3 (gcc objective c compiler) and libobjc2 (objective c runtime library) installed. What else do I need in order to compile objective c? What library is -lobjc talking about, how can I install it?

---

### Post by SevenMachines on 2009-12-07
$sudo apt-get install gobjc 
should install all the dependencies you need for a simple objc program (including libobjc2)

You dont need the -lobjc flag either (though the library should be found if you do include it)
$ gcc -o hello hello.m

If your still having problems can you post the full gcc output and any more information you have to hand.

---

### Post by diegoallen on 2009-12-08
The thing is that im not using regular gcc but the arm-apple-darwin9-gcc for the iphone. So when I install objective c libs the compiler I`m using doesn`t find them. How can I know where is "arm-apple-darwin9-gcc" searching for header files and libs? That way I`m gonna be able to copy them manually. I tryed using -I/path/to/where/objc.h/is but i got the same error.

---

### Post by SevenMachines on 2009-12-09
ah, i see, i assume you have the arm/iphone objc libraries installed somewhere on your system (and the iphone toolchain in general ) rather than for i386/amd64? 
$gcc -print-search-dirs
should give useful information on default search paths

---

### Post by diegoallen on 2009-12-10
Yes I have the toolchain and libs needed my only problem is that gcc doesnt seem to find them. I`ll try "gcc -print-search-dirs" and post my results. thanks for the help so far..

---

### Post by Some Penguin on 2009-12-17
-I is only for #include pragmas -- header files.
-L is what you want for specifying directories for the linker to search.

---

