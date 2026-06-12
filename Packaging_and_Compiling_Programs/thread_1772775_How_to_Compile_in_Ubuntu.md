---
title: "How to Compile in Ubuntu?"
date: 2011-06-01
forum: Packaging and Compiling Programs
---

### Post by lakshmen on 2011-06-01
I am not sure how to compile in Ubuntu... can anyone help?

---

### Post by lemuriaX on 2011-06-01
Here's one resource that might help:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by lakshmen on 2011-06-01
hi, if i wrote a code in ubuntu how to compile? is it the same?

---

### Post by sj1410 on 2011-06-01
is it a C/C++ code, than you need gcc

for example

gcc myprg.c -o myprg.o

to run

./myprg.o


hope this helps

---

### Post by lakshmen on 2011-06-01
just have a qn: what is the difference between cmake and make?? does it make a difference if i use make instead of this?

---

### Post by lakshmen on 2011-06-02
Hi guys, i am trying to compile a file that uses the OpenKinect driver. when i do so, i get this error
 
libfreenect.hpp:29: fatal error: libfreenect.h: No such file or directory
compilation terminated.

but i have already included the libfreenect.h file in the same directory. what should i do?

---

### Post by lakshmen on 2011-06-02
any help please?

---

### Post by uRock on 2011-06-02
Moved to *Packaging and Compiling Programs*.

Please wait until 24 hours of dormancy before bumping your thread.

Regards,
uRock

---

### Post by SevenMachines on 2011-06-03
You need to post more about what you are doing, where you have installed openkinect to. Have you included the directory with libfreenect.h? 
gcc -I/path/to/include/files -o myprogram myprogram.c

Addtionally i'd say, if libfreenect.hpp is your own file, rename it. .hpp and .h are extensions for header files and although not a problem to have libfreenect.h and libfreenect.hpp  its very confusing and bad form.

Also, openkinect has a ppa (see [http://openkinect.org/wiki/Getting_Started#Ubuntu](http://openkinect.org/wiki/Getting_Started#Ubuntu)). Unless you have some reason to compile it yourself, dont. Just add the ppa and install libfreenect-dev instead, this will (or should!) install its header files to the system directories which the compiler looks in by default so you wouldnt need to do anything on the command line to find them.

---

