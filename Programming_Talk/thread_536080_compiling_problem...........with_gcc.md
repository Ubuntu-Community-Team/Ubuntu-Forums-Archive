---
title: "compiling problem...........with gcc"
date: 2007-08-27
forum: Programming Talk
---

### Post by fyny on 2007-08-27
friend i am newer in ubuntu.............
at the time of compiling a c file  i am getting the error message below.........
```
banti@root:~$ ls
Desktop  ex1.css  Examples  testcss  type.html  type.html~  welcome.c
banti@root:~$ make welcome
cc     welcome.c   -o welcome
welcome.c:1:19: error: stdio.h: No such file or directory
welcome.c: In function ‘main’:
welcome.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
make: *** [welcome] Error 1
```
------------------------------------------------------------------------------------------
```
banti@root:~$ gcc -o welcome welcome.c
welcome.c:1:19: error: stdio.h: No such file or directory
welcome.c: In function ‘main’:
welcome.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

```
-------------------------------------------------------------------------------------
my gcc version is...........
```
banti@root:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

```
then plz tell me what is the exact reason of this? is it the problem of ubuntu gcc or there is a another way to compile...........:confused:

---

### Post by LaRoza on 2007-08-27
```

sudo aptitude install build-essential

```

This will get all the headers, and other essentials. I don't know why it isn't installed with Ubuntu, it is on the cd.

---

### Post by Lord Illidan on 2007-08-27
Another thing...are you sure your C program is correct? Post it here to be sure.

---

