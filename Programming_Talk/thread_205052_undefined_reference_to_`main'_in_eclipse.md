---
title: "undefined reference to `main' in eclipse"
date: 2006-06-27
forum: Programming Talk
---

### Post by jinxjinx on 2006-06-27
im using the c++ plug in for eclipse and im tyring to compile and run my hello world program and i get this:


**** Full rebuild of configuration Debug for project test ****

make -k clean all 
rm -rf  ./testmain.d ./testmain.o  test
 
Building file: ../testmain.cpp
Invoking: GCC C++ Compiler
gcc -O0 -g3 -Wall -c -fmessage-length=0 -otestmain.o ../testmain.cpp
Finished building: ../testmain.cpp
 
Building target: test
Invoking: GCC C++ Linker
gcc -otest ./testmain.o
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [test] Error 1
make: Target `all' not remade because of errors.
Build complete for project test


my hello world program is here:

#include <iostream>
using namespace std;
void main()
{
     cout << "Hello World";
}

any help would be great thanks!

---

### Post by Stromham on 2006-06-27
yes dont use void main its bad practice use int main () {} also are there and log  outputs for the failure?

---

### Post by Thirsteh on 2006-06-27
I don't have the ability to test this out thoroughly at the moment, I do have one suggestion however;

Change the main void to an int :)

#include <iostream>
using namespace std;
int main()
{
cout << "Hello World";
}

This should work. If it doesn't, 'gcc -otest' doesn't work with C++ perhaps?

---

### Post by scxtt on 2006-06-27
try using g++ instead of gcc ...

---

### Post by jinxjinx on 2006-06-27
must have been a bug. worked after i reset eclipse.
thanks

---

### Post by Rinnan on 2008-11-06
Yes, I had this same problem, and this same solution worked.

---

### Post by psa3ebres on 2012-06-07
What i have noticed is that whenever i create a new Project and a source file, I have to save the source file before I build, otherwise i get the **undefined reference to 'main' **error. Hope this help.

---

