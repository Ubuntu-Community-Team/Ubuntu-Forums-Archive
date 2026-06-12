---
title: "[SOLVED] cannot create executables. build-essential is installed."
date: 2007-11-02
forum: Packaging and Compiling Programs
---

### Post by timseal on 2007-11-02
I've read everything here, and googled extensively.
I still get this error whenever trying to compile anything.
I've got build-essential installed.

Here's what seems to be the relevant part of config.log:

```
configure:3147: $? = 0
configure:3154: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3157: $? = 0
configure:3164: gcc -V >&5
gcc: '-V' option must have argument
configure:3167: $? = 1
configure:3190: checking for C compiler default output file name
configure:3217: gcc    conftest.c  >&5
gcc: error trying to exec 'cc1': execvp: No such file or directory
configure:3220: $? = 1
configure:3258: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "transmission"
| #define PACKAGE_TARNAME "transmission"
| #define PACKAGE_VERSION "0.91"
| #define PACKAGE_STRING "transmission 0.91"
| #define PACKAGE_BUGREPORT "http://transmission.m0k.org/trac/newticket"
| #define PACKAGE "transmission"
| #define VERSION "0.91"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3265: error: C compiler cannot create executables
See `config.log' for more details.

```

I'm getting rather desperate now.  Help?

---

### Post by mlind on 2007-11-02
What application are you compiling?
According to the error message, you're missing 'cc1' binary.

What's the output of
```

slocate -r /cc1$

```

You probably need to install one of the following cpp packages which provide cc1
```

cpp-3.3: usr/lib/gcc-lib/i486-linux-gnu/3.3.6/cc1
cpp-3.4: usr/lib/gcc/i486-linux-gnu/3.4.6/cc1
cpp-4.1: usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
cpp-4.1: usr/lib/gcc/i486-linux-gnu/4.1/cc1
cpp-4.2: usr/lib/gcc/i486-linux-gnu/4.2/cc1

```

---

### Post by timseal on 2007-11-02
slocate -r /cc1$ gives nothing.
I have cpp-4.1 installed, in fact I just reinstalled it.
I have the file /usr/lib/gcc/i486-linux-gnu/4.1.2/cc1 on my system.
I'm trying to compile Transmission, but it happens for everything.

---

### Post by mlind on 2007-11-02
You should take the newest trasmission package from Debian unstable using *apt-get source transmission*. It's already packaged so you just need compile and install the resulting .deb packages.


Here's what I get if I compile the transmission in Debian unstable. It seems to work okay.
```

configure:3147: $? = 0
configure:3154: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:3157: $? = 0
configure:3164: gcc -V >&5
gcc: '-V' option must have argument
configure:3167: $? = 1
configure:3190: checking for C compiler default output file name
configure:3217: gcc -Wall -g -O2  -Wl,-z,defs conftest.c  >&5
configure:3220: $? = 0
configure:3258: result: a.out
configure:3275: checking whether the C compiler works
configure:3285: ./a.out
configure:3288: $? = 0
configure:3305: result: yes
configure:3312: checking whether we are cross compiling
configure:3314: result: no
configure:3317: checking for suffix of executables
configure:3324: gcc -o conftest -Wall -g -O2  -Wl,-z,defs conftest.c  >&5
configure:3327: $? = 0
configure:3351: result: 
.
.

```
(I wonder if you need to have something installed that is Recommended by build-essential package depends, like libc6-dev ?)

---

### Post by timseal on 2007-11-02
The point is not that I can't build Transmission, it's that I can't build ANYTHING at all.

---

### Post by mlind on 2007-11-02
> **timseal said:**
> The point is not that I can't build Transmission, it's that I can't build ANYTHING at all.

right, how about
```

sudo aptitude purge build-essential
sudo aptitude install build-essential

```
?

---

### Post by timseal on 2007-11-02
OK, tried it, no difference.

---

### Post by lolindrath on 2007-11-02
I checked my box, the cc1 file is supplied by the cpp-4.2 package so try:

```
sudo apt-get install cpp-4.2
```

This package should've been supplied by build-essential so I'm kind of thinking something got hosed.

I also thought I'd mention, Transmission is available on apt-get.

---

### Post by mlind on 2007-11-02
> **lolindrath said:**
> I checked my box, the cc1 file is supplied by the cpp-4.2 package so try:

```
sudo apt-get install cpp-4.2
```

This package should've been supplied by build-essential so I'm kind of thinking something got hosed.

I also thought I'd mention, Transmission is available on apt-get.

strange, I only have cpp which provides cpp-4.1 and I don't have issues timseal is describing.
(using Gutsy)

---

### Post by timseal on 2007-11-02
Should have tried this earlier, but oh well.

```
#include<stdio.h>

main()
{
    printf("Hello World");
}

```

```
tim@tkalaptop:~/src$ gcc hello.c -o hello
gcc: error trying to exec 'ld': execvp: No such file or directory
tim@tkalaptop:~/src$ g++ hello.c -o hello
g++: error trying to exec 'ld': execvp: No such file or directory

```

It's the same error that's in config.log.  So I'd say there's something quite fundamentally wrong/missing in the compiler setup.

---

### Post by mlind on 2007-11-02
hey, do you have g++ package installed (especially  g++-4.1) ?

/edit scratch that.. looks like something else is broken. Does running ldconfig as root work okay?

---

### Post by lolindrath on 2007-11-02
> **mlind said:**
> strange, I only have cpp which provides cpp-4.1 and I don't have issues timseal is describing.
(using Gutsy)

I have cpp-3.3, cpp-3.4, cpp-4.1 and cpp-4.2 but I've upgraded twice so my package structure is probably pretty crazy.

I also had no problems compiling Transmission except for needing to install libssl-dev.

--Lolindrath

---

### Post by timseal on 2007-11-02
g++ and g++-4.1 are both installed.
I'm still running Feisty, would love to upgrade but I have one of those Ubuntu Dells, so I'm waiting for Dell's iso.

---

### Post by timseal on 2007-11-02
> **mlind said:**
> 
/edit scratch that.. looks like something else is broken. Does running ldconfig as root work okay?

```

tim@tkalaptop:~/src$ sudo ldconfig
ldconfig: Renaming of /etc/ld.so.cache~ to /etc/ld.so.cache failed: No such file or directory
```

Not sure what this could mean... any ideas?

---

### Post by timseal on 2007-11-02
I noticed that I didn't have /usr/bin/ld so I reinstalled binutils, I have ld now.  I tried to compile hello.c again, and got a different error:
```
ld: crtbegin.o: No such file: No such file or directory
```
So I'll go looking for that..

---

### Post by timseal on 2007-11-02
YES!
I reinstalled gcc-4.1 which gave me a few extra files in /usr/lib/gcc/i486-linux-gnu/4.1.2/.   Everything seems to compile now.

Now, how the heck did my system get messed up like that???

---

