---
title: "linking headaches"
date: 2009-10-06
forum: Programming Talk
---

### Post by Houman on 2009-10-06
hi all;

As part of a project I have to write a program that is completely cross platform in C/C++, so i have had to make sure it works in both win and linux;

recently I am linking against a program and it works fine in linux but when i compile it in cygwin it is giving me an "undefined reference" error during the final linkage stage, even though i have the library and my makefile points to it. any hints as to why this could be happening is appreciated;

here is the compile error messages : 
```

make  all-am
make[1]: Entering directory `/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd'
g++ -Wall -O3  -DNDEBUG -g -O2 -lnetpbm  -o recalckeys.exe  recalckeys.o image.o keypoint.o
image.o: In function `_ZN5ImageC1EPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:57: undefined reference to `_pgm_readpgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:70: undefined reference to `_pm_freearray'
image.o: In function `_ZN5ImageC2EPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:57: undefined reference to `_pgm_readpgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:70: undefined reference to `_pm_freearray'
image.o: In function `_ZN5Image5writeEPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:202: undefined reference to `_pm_allocarray'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:214: undefined reference to `_pgm_writepgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:216: undefined reference to `_pm_freearray'
collect2: ld returned 1 exit status
make[1]: *** [recalckeys.exe] Error 1
make[1]: Leaving directory `/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd'
make: *** [all] Error 2

```

and this is weird because when i do:

```
 
$ nm libnetpbm.a | grep _pm_freearray
00002000 T _pm_freearray

```

so the symbol that is suppose to not be found really does exist in the library that my makefile is pointing to, so why isnt it working? :(

thank you 

Houman

---

### Post by Arndt on 2009-10-07
> **Houman said:**
> hi all;

As part of a project I have to write a program that is completely cross platform in C/C++, so i have had to make sure it works in both win and linux;

recently I am linking against a program and it works fine in linux but when i compile it in cygwin it is giving me an "undefined reference" error during the final linkage stage, even though i have the library and my makefile points to it. any hints as to why this could be happening is appreciated;

here is the compile error messages : 
```

make  all-am
make[1]: Entering directory `/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd'
g++ -Wall -O3  -DNDEBUG -g -O2 -lnetpbm  -o recalckeys.exe  recalckeys.o image.o keypoint.o
image.o: In function `_ZN5ImageC1EPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:57: undefined reference to `_pgm_readpgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:70: undefined reference to `_pm_freearray'
image.o: In function `_ZN5ImageC2EPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:57: undefined reference to `_pgm_readpgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:70: undefined reference to `_pm_freearray'
image.o: In function `_ZN5Image5writeEPKc':
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:202: undefined reference to `_pm_allocarray'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:214: undefined reference to `_pgm_writepgm'
/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd/image.cc:216: undefined reference to `_pm_freearray'
collect2: ld returned 1 exit status
make[1]: *** [recalckeys.exe] Error 1
make[1]: Leaving directory `/cygdrive/c/Users/Houman/Desktop/pcasift-0.91nd'
make: *** [all] Error 2

```

and this is weird because when i do:

```
 
$ nm libnetpbm.a | grep _pm_freearray
00002000 T _pm_freearray

```

so the symbol that is suppose to not be found really does exist in the library that my makefile is pointing to, so why isnt it working? :(

thank you 

Houman

You can try these things: 1) Put the -lnetpbm at the end; 2) Make sure gcc finds libnetpbm by using a -L directive (but it ought to give an error if it doesn't find it); 3) Use 'ranlib' on libnetpbm.a, if it's something you built yourself.

The ranlib thing is something very old that perhaps isn't needed anywhere anymore - I don't know.

You might have several copies of lib

---

### Post by Zugzwang on 2009-10-07
You have fallen into the [name mangling]("http://en.wikipedia.org/wiki/Name_mangling") trap. Make sure that in your C++-source code, when referring to C functions, they are declared as being extern "C". See the wikipedia article linked to above for details.

---

### Post by dwhitney67 on 2009-10-07
It could also be that the library is specified before the object files in the Make statement.

This statement:
```

g++ -Wall -O3  -DNDEBUG -g -O2 -lnetpbm  -o recalckeys.exe  recalckeys.o image.o keypoint.o

```
should not contain compiler flags; at this point the Makefile has already generated the object files, and now it is time to link.

The statement should be something like:
```

g++ -o recalckeys.exe  recalckeys.o image.o keypoint.o -lnetpbm

```
Personally, I prefer to put the -o option at the end, but it is not required.

---

### Post by Houman on 2009-10-07
Hi folks;

thank you for the replies. When I changed the -lnetpbm and put it at the end it worked fine. I don't quite understand why it didn't want me to put it at the beginning.

thanks again, I am now linking successfully :)

Houman

---

### Post by Arndt on 2009-10-08
> **Houman said:**
> Hi folks;

thank you for the replies. When I changed the -lnetpbm and put it at the end it worked fine. I don't quite understand why it didn't want me to put it at the beginning.

thanks again, I am now linking successfully :)

Houman

The traditional simplistic way for a Unix linker to work is to process libraries and object files from left to right. When a library is encountered, it is used to resolved what currently unresolved symbols it can, and then forgotten.

---

### Post by Houman on 2009-10-08
hello Arndt;

that is very helpful info, thank you! I dont know how come i never knew that in spite of programming on linux for years :S

H

---

### Post by bagussetya on 2012-01-31
Hi all, 

My name is Bagus Setya Rintyarna. I'm using PCA-SIFT for my  master exercise. I'm newbie in programming as well as in ubuntu. I read some reference that PCA-SIFT need keypoint  detector code and it should be merged to PCA-SIFT source code (from Yan  Ke). Would anyone give me any suggestion how to merge the code ? I try to  compile PCA-SIFT code in ubuntu and got this error :

if g++ -DHAVE_CONFIG_H -I. -I. -I.    -Wall -O3  -DNDEBUG -g -O2 -MT  image.o -MD -MP -MF ".deps/image.Tpo" -c -o image.o image.cc; \
    then mv -f ".deps/image.Tpo" ".deps/image.Po"; else rm -f  ".deps/image.Tpo"; exit 1; fi
image.cc:18:22: error: pgm.h: No such file or directory
image.cc: In constructor ‘Image::Image(const char*)’:
image.cc:54: error: ‘gray’ was not declared in this scope
image.cc:54: error: expected ‘;’ before ‘maxval’
image.cc:55: error: ‘pixels’ was not declared in this scope
image.cc:57: error: ‘maxval’ was not declared in this scope
image.cc:57: error: ‘pgm_readpgm’ was not declared in this scope
image.cc:70: error: ‘pgm_freearray’ was not declared in this scope
image.cc: In member function ‘void Image::write(const char*)’:
image.cc:202: error: ‘gray’ was not declared in this scope
image.cc:202: error: ‘pixels’ was not declared in this scope
image.cc:202: error: ‘pgm_allocarray’ was not declared in this scope
image.cc:214: error: ‘pgm_writepgm’ was not declared in this scope
image.cc:216: error: ‘pgm_freearray’ was not declared in this scope
make[1]: *** [image.o] Error 1
make[1]: Leaving directory `/home/bagus/pcasift-0.91nd'
make: *** [all] Error 2

---

### Post by overdrank on 2012-01-31
Hi and welcome, please start a new thread with your issues. Back to sleep thread. Thread closed.

---

