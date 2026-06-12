---
title: "statically link program which uses lapack"
date: 2009-03-31
forum: Programming Talk
---

### Post by lost_prophet on 2009-03-31
Hello,

I am writing a program, which uses the lapack libraries. I need to build a static version of my program, since I want to run it on different computers, which probably do not have installed all the libraries I need.

I have already successfully build my program with -static on a debian box with gcc 4.1.2, since the library libg2c.a was available on this box.

Unfortunately Ubuntu doesn't provide this library. So my question is, which library could I use instead of g2c? By the way dynamic linking works fine on Ubuntu. The program is then linked with libgfortran.so, which is also not available as a static library.

Thanks for your reply,


lost_prophet

---

### Post by Arndt on 2009-03-31
> **lost_prophet said:**
> Hello,

I am writing a program, which uses the lapack libraries. I need to build a static version of my program, since I want to run it on different computers, which probably do not have installed all the libraries I need.

I have already successfully build my program with -static on a debian box with gcc 4.1.2, since the library libg2c.a was available on this box.

Unfortunately Ubuntu doesn't provide this library. So my question is, which library could I use instead of g2c? By the way dynamic linking works fine on Ubuntu. The program is then linked with libgfortran.so, which is also not available as a static library.

Thanks for your reply,


lost_prophet

I don't use any Fortran packages, so I may be misunderstanding the question, but there exists a package libg2c0 on Ubuntu.

---

### Post by lost_prophet on 2009-03-31
Thanks for the comment. This package just contains a dynamic library libg2c.so.0 but not a static version of this library. Thus this package wouldn't help me.

What I don't understand is, why the package gfortran-4.3 doesn't provide a static library gfortran.a additionally to gfortran.so. 

What I should probably mention is that I use gcc4.3.2 for compiling my c++ program.

Can anybody bail me out? Has anybody done static linking with a fortran library? Probably I am thinking too complicated?

thanks


l_p

---

### Post by clustermonkey on 2009-03-31
A lot of distros don't include static libraries.  I've had
to pull down the sources and compile the libs a couple of
times.  I guess my question is that if you have already 
compiled the program static under Debian, why do you need 
to compile it under Ubuntu?

---

### Post by lost_prophet on 2009-03-31
I installed gfortran-4.3, which includes libgfortran.a.

---

### Post by nvteighen on 2009-03-31
Just something... the static libraries are usually included in the *-dev packages.

---

### Post by eye208 on 2009-04-01
> **lost_prophet said:**
> I need to build a static version of my program, since I want to run it on different computers, which probably do not have installed all the libraries I need.
Instead of building a static version, you can also bundle the required libraries with your program. You can specify an alternate library search path, e.g. the current directory, either by setting the environment variable LD_LIBRARY_PATH when running the program, or by storing that path inside the ELF executable using the -rpath link option.

Here's a (very simple) example using hello.c:
```
#include <stdio.h>

int main() {
        printf("Hello World!\n");
        return 0;
}
```
After compiling this program, the output of ldd typically looks like this:
```
	linux-gate.so.1 =>  (0xb7fcc000)
	libc.so.6 => /lib/i686/cmov/libc.so.6 (0xb7e5d000)
	/lib/ld-linux.so.2 (0xb7fcd000)
```
If you copy libc.so.6 to the current directory and run
```
LD_LIBRARY_PATH=. ldd hello
```
the output will look like this:
```
	linux-gate.so.1 =>  (0xb7f1e000)
	libc.so.6 => ./libc.so.6 (0xb7dc1000)
	/lib/ld-linux.so.2 (0xb7f1f000)
```
If you run the program with LD_LIBRARY_PATH set this way, it will use the local copy of libc.so.6 instead of the one in /lib.

To hardcode the search path into the program, compile it like this:
```
gcc -o hello -Wl,-rpath,. hello.c
```
Now you don't need to set LD_LIBRARY_PATH any more. The program will always prefer libraries in the current directory, if available.

---

