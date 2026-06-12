---
title: "Don't know how to compile multiple files using CUnit"
date: 2019-08-29
forum: Programming Talk
---

### Post by rajvishar on 2019-08-29
I have files with the name raj_test.h and raj_test.c inside the folder ~/raj_lib/master/tests/raj and CUnit is located at ~/raj_lib/CUnit-2.1-3
[COLOR=#000000][FONT=verdana]
I ollowed following steps:
Step 1: Download CUnit package from Source Forge.

Step 2: Find where you saved the package on your system, and uncompress it:

Step 3: Go into the CUnit directory.

Step 4: Run the following sequence of commands:
mkdir -p $HOME/local
./configure --prefix=$HOME/local
make clean
make
make install

Step 5: Goto the directory $HOME/local. Verify that you have the following sub-directories: doc, include, lib, and share. Each of these should have the products you seek.

Step 6. To build an application using CUnit, something like this is used:
gcc -Wall -I$HOME/local/include MyProg.c -L$HOME/local/lib -lcunit -o myprog

Also, included CUnit header files such as:
#include <CUnit/Basic.h>


[/FONT][/COLOR]

When I try to run following command:
gcc -Wall -I$HOME/local/include raj_test.c -L$HOME/local/lib -lcunit -o raj_test


I get an error as follows:
gcc: error: raj_test.c: No such file or directory


Where should I run the above command? Should I be running the above command at ~/raj_lib/master/tests/raj ? Or where CUnit is located?


Also, since I have .h and .c files, how can I combine both to get required binary.



Regards,
Raj

---

### Post by TheFu on 2019-08-29
~/raj_lib/CUnit-2.1-3 to build the library first.  Then move to the directory with the C file you want to compile that links with the cunit library.

The compile command you show above assumes that the libcunit.a file has been built and placed somwhere else already.  Has it?

Programmers need to be very clear when compiling which directory they are in.  
```
gcc: error: raj_test.c: No such file or directory
```
says you aren't in the same directory.

---

### Post by spjackson on 2019-08-30
> **rajvishar said:**
> 
When I try to run following command:
gcc -Wall -I$HOME/local/include raj_test.c -L$HOME/local/lib -lcunit -o raj_test


I get an error as follows:
gcc: error: raj_test.c: No such file or directory


Where should I run the above command? Should I be running the above command at ~/raj_lib/master/tests/raj ? Or where CUnit is located?


Also, since I have .h and .c files, how can I combine both to get required binary.

The above command is looking for raj_test.c in the current working directory. It fails because this file is not there. You need to run it from the directory where raj_test.c is located.

.h files would not normally be compiled directly. They are included by #include directives within .c files.

---

