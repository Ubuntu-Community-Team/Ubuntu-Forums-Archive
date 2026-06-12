---
title: "Quick help with compiling..."
date: 2009-03-06
forum: Programming Talk
---

### Post by gafferuk on 2009-03-06
Hi, im new to lixux but not c programming.

Im trying to use The Synthesis ToolKit in C++ (STK) but im having trouble using it.

The IDE im using is geany. And im using the following includes;
#include <string>
#include <iostream>
#include <sstream>
#include <vector>

when i build im receiving errors like:
/usr/include/stk/include/Stk.h:56:18: error: string: No such file or directory

what library do i have to include to use these headers and what is the build command?

im using:
compile:  gcc -Wall -c  -D__LITTLE_ENDIAN__  "-I/usr/include/stk %f"  -lstk

and for build im using;
  gcc -Wall -o  "%e" "-I/usr/include/stk/include" "%f"  -lstk

Thanks for your time, much appreciated!! :)

---

### Post by dwhitney67 on 2009-03-06
Note that C and C++ are not the same.

If you indeed have STK header files in /usr/include/stk, then you should be able to verify such by examining that folder.  Start by looking for Stk.h.

Note the Linux filenames are case sensitive.

If the Stk.h is in /usr/include/stk, then in your source files
#include <stk/Stk.h> should suffice.

If you wish to specify only #include <Stk.h>, then you would require the -I /usr/include/stk when you compile your source modules.

---

### Post by gafferuk on 2009-03-06
my app compiles fine but does not build. I have the stk header files in the right place, so ok there.



its finding stk header file fine but is complaining about #include <string> and more.

im guessing it needs a library? any ideas?

---

### Post by tneva82 on 2009-03-06
> **gafferuk said:**
> and for build im using;
  gcc -Wall -o  "%e" "-I/usr/include/stk/include" "%f"  -lstk

Thanks for your time, much appreciated!! :)

Hum hum. Not sure but IIRC gcc is C-compiler while you are using C++ headers. Try g++ instead. Atleast that solved issue for me though maybe -I is supposed to do that anyway.

---

### Post by gafferuk on 2009-03-06
> **tneva82 said:**
> Hum hum. Not sure but IIRC gcc is C-compiler while you are using C++ headers. Try g++ instead. Atleast that solved issue for me though maybe -I is supposed to do that anyway.


I see, thanks for the info, im trying it now once i instasll g++ that is

---

### Post by eye208 on 2009-03-06
> **gafferuk said:**
> my app compiles fine but does not build.

its finding stk header file fine but is complaining about #include <string> and more.
These are contradicting statements. As long as the compiler complains about missing headers, your app does not compile.

---

### Post by gafferuk on 2009-03-06
Ive insalled g++ and i am geting a bit  closer, but is complaining:

im using "Mint" a ubuntu based disribuion.
Ive installed the stk(the synthesis tool kit) sdk using the package manager and it insalled ok.

BUT when I compile my app with the following it spits out an error
g++ -Wall -D__LITTLE_ENDIAN__ -I/usr/include/stk/include -o mainapp mainapp.c -libstk

the error i get is:
/usr/bin/ld: cannot find -libstk

the compile arguments is what is said in the install guide.

any ideas what im doing wrong?

---

### Post by dwhitney67 on 2009-03-06
try -lstk

You may also want to verify that libstk* exists in /usr/lib or /usr/local/lib.

---

### Post by gafferuk on 2009-03-06
> **dwhitney67 said:**
> try -lstk

You may also want to verify that libstk* exists in /usr/lib or /usr/local/lib.

I tried -lsdk but no joy.

I looked in usr/lib and found 2 files:
libsdk.so.0 & libsdk.so.0.4.1.3

are these ok? thanks.

---

### Post by tneva82 on 2009-03-06
Edit: Scrap that. Misread library.

---

### Post by gafferuk on 2009-03-06
im wandering if the "package manager" has installed the rpm/deb package correctly? after install it did not include the include files for the library so i had to download the src code from the net and use the include files from that and paste them to usr/include/stk.
if the include files did not install does that mean the lib file was not registered with whatever?

any ideas, im real stuck, this is my first project with linux as used to program with windows lol.

I started all over again but it's still the same, i get the following error:
/usr/bin/ld: cannot find -lstk

heres the install instructions if anyone can help me?:
[http://ccrma.stanford.edu/software/stk/compile.html](http://ccrma.stanford.edu/software/stk/compile.html)

if anyone knows of a better library than "the synthesis toolkit" then please let me know, ill give it a try.

Thanks.
Paul.

---

