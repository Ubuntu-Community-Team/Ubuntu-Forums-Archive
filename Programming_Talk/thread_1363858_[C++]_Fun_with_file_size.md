---
title: "[C++] Fun with file size"
date: 2009-12-25
forum: Programming Talk
---

### Post by kahumba on 2009-12-25
I noticed that g++ even for smallest snippets outputs around 10KB files:
```

#include <cstdio>

int main() {
	printf("Hello world!\n");
	return 0;
}

```
yields almost 10KB, that is, about 100 times the size of the source code. Just for fun, is it possible to create a C++ hello world app under say 2KB without doing assembly?
g++ -Os didn't help.

---

### Post by dwhitney67 on 2009-12-25
I'm not sure why your program is coming out at 10KB, and I'm not quite sure why you care.

I was not able to conjure up a 2KB program, but using the more traditional C++ code as shown below, I came up with 8.9KB.
```

#include <iostream>

int main()
{
   std::cout << "Hello World!" << std::endl;
   return 0;
}

```

---

### Post by Habbit on 2009-12-25
Code for global initialization and termination of the C++ runtime environment, plus ELF headers and (maybe) debug information might do that. Try to compile the same code (including "stdio.h" instead of "cstdio", of course) with gcc and check the size.

---

### Post by Ferrat on 2009-12-25
> **dwhitney67 said:**
> I'm not sure why your program is coming out at 10KB, and I'm not quite sure why you care.


Not care about a ~500% increase? o.O
While the notion of unlimited RAM, diskspace etc seems to get stronger and stronger every day I'm glad to see at least someone care about memory

---

### Post by Zugzwang on 2009-12-25
Ok, let's have a look at the details for a more complete answer. Compiling the code with "gcc" instead of "g++" (and exchanging "cstdio" by "stdio.h") yields a reduction to 9144 bytes. Well, this is the case at least on my computer (Ubuntu 9.04, 32 bit), your numbers may be a little bit different.

Ok, now if this is not enough, we try some additional trick and run "strip a.out". This strips some unnecessary symbols from the executable. And hooray, we get 5652 bytes. However, I'm not sure if this stuff is actually loaded into memory when loading the program. Ok, now this is still 5 kb for a very smallish program.

So let's have a look at the code that gcc actually produces. For this, we run "gcc -S test.c" (assuming that I've saved the original source code to "test.c"). This will create an assembler source file "test.S". It looks as follows:
```

        .file   "test.c"
        .section        .rodata
.LC0:
        .string "Hello world!"
        .text
.globl main
        .type   main, @function
main:
        leal    4(%esp), %ecx
        andl    $-16, %es
        pushl   -4(%ecx)
        pushl   %ebp
        movl    %esp, %ebp
        pushl   %ecx
        subl    $4, %esp
        movl    $.LC0, (%esp)
        call    puts
        movl    $0, %eax
        addl    $4, %esp
        popl    %ecx
        popl    %ebp
        leal    -4(%ecx), %esp
        ret
        .size   main, .-main
        .ident  "GCC: (Ubuntu 4.3.3-5ubuntu4) 4.3.3"
        .section        .note.GNU-stack,"",@progbits
```
So it doesn't look too overcrowded. Note that a string is added which tells about the compiler version. But this is only a small overhead.

So the question remains: Where does the remaining overhead come from? For this, we try a different approach: "gcc -g test.c; valgrind --tool=callgrind ./a.out" and then we run kcachegrind on the generated callgrind.<PID>.out file. We will see that "a.out" actually contains three functions: "__libc_csu_init", "0x08048310" and "main". We will see that actually a lot of time is spent in the the second function and the source is located in some file "start.S" which kcachegrind cannout find. 

So we reach the conclusion: Some overhead is caused by the linker which links against some code for the start-up procedure of the application. However, every program will only need this overhead once, so its relatively small amount should normally be OK in almost all cases. In all cases, if you care about your application's size, strip the unnecessary symbols from it!

---

### Post by djurny on 2009-12-25
you can also try to strip out all symbols and crud..

```

$ g++ helooworld.cpp -o helloworld
$ ll helloworld
-rwxr-xr-x 1 djurny djurny 11011 2009-12-25 14:08 helloworld*
$ strip helloworld
$  ll helloworld
-rwxr-xr-x 1 djurny djurny 6400 2009-12-25 14:08 helloworld*

```

this results in an executable of merely 6400 bytes.. (x86_64, g++ 4.3)
> Not care about a ~500% increase? o.O
While the notion of unlimited RAM, diskspace etc seems to get stronger and stronger every day I'm glad to see at least someone care about memory
hear hear :)

---

### Post by dwhitney67 on 2009-12-25
> **Ferrat said:**
> Not care about a ~500% increase? o.O
While the notion of unlimited RAM, diskspace etc seems to get stronger and stronger every day I'm glad to see at least someone care about memory

There's other information that is included within the application that makes it easier to identify, debug, etc.  Some of that stuff can be stripped away, but still, one is going to have an app that includes relevant information as to what version of GCC was used to build it, what OS was used, the library dependencies, etc.

I've written s/w in the past in which I only had 256KB of ROM storage where the executable resided, and even less space of RAM.  This was 20 years ago.  Are you telling me that someone has a platform where they have less than this?  Are chips even made this small anymore?

---

### Post by djurny on 2009-12-25
> **dwhitney67 said:**
> There's other information that is included within the application that makes it easier to identify, debug, etc.  Some of that stuff can be stripped away, but still, one is going to have an app that includes relevant information as to what version of GCC was used to build it, what OS was used, the library dependencies, etc.

I've written s/w in the past in which I only had 256KB of ROM storage where the executable resided, and even less space of RAM.  This was 20 years ago.  Are you telling me that someone has a platform where they have less than this?  Are chips even made this small anymore?

we worked on single page nandflash bootloaders (16kib pages) for a while, even 80c51 based microcontrollers (< 4kib ram), so yes, there are platforms with even lesser requirements :)
(and yes, all that went into consumer electronics over the past 2 years)

---

### Post by dwhitney67 on 2009-12-25
> **djurny said:**
> we worked on single page nandflash bootloaders (16kib pages) for a while, even 80c51 based microcontrollers (< 4kib ram), so yes, there are platforms with even lesser requirements :)
(and yes, all that went into consumer electronics over the past 2 years)

Please, don't confuse RAM with ROM.  The former is used during runtime of an executable; the latter is for storage (of the executable, data, etc).

In embedded systems, when you declare a variable on the stack or get it from the heap, it is coming from RAM... not ROM.

---

### Post by nvteighen on 2009-12-25
For your interest, I've managed to reduce the standard **C** Hello World's size to 2.8 KB :P Compiling with:

```

ugi@UGI:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 4.3.4-6' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.4 (Debian 4.3.4-6) 

```

The compiled version takes 4.4 KB. Stripping it gives me 2.8 KB :)

The **C++** version (using iostream, not cstdio) takes 6.0 KB in my box; 3.9 KB after stripping. My g++ compiler is:
```

ugi@UGI:~/Desktop$ g++ -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 4.3.4-6' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.4 (Debian 4.3.4-6) 

```

---

### Post by djurny on 2009-12-25
> **dwhitney67 said:**
> Please, don't confuse RAM with ROM.  The former is used during runtime of an executable; the latter is for storage (of the executable, data, etc).

In embedded systems, when you declare a variable on the stack or get it from the heap, it is coming from RAM... not ROM.

lets hope all developers worldwide know this difference too and also try to focus on knowing your platform instead of coding away and being surprised that porting applications to 'smaller' platforms can take so much time :)

---

### Post by Arndt on 2009-12-25
> **djurny said:**
> you can also try to strip out all symbols and crud..

```

$ g++ helooworld.cpp -o helloworld
$ ll helloworld
-rwxr-xr-x 1 djurny djurny 11011 2009-12-25 14:08 helloworld*
$ strip helloworld
$  ll helloworld
-rwxr-xr-x 1 djurny djurny 6400 2009-12-25 14:08 helloworld*

```

this results in an executable of merely 6400 bytes.. (x86_64, g++ 4.3)

hear hear :)

Note that stripping save a little disk space, but doesn't change what is loaded when the program runs.

---

### Post by falconindy on 2009-12-25
This is probably pertinent, although it does get into assembly fairly quickly.

[http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html](http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html)

Still a fun read.

---

### Post by Can+~ on 2009-12-25
On a sidenote, let's see what happens with other languages:

Haskell (using the Glasgow Haskell Compiler):
[PHP]main = do
	print "Hello World!"[/PHP]

```
ghc helloworld.hs
```

Output:
a.out 594.3 KB (608589 bytes)

Holy crap.

---

### Post by nvteighen on 2009-12-25
> **Can+~ said:**
> On a sidenote, let's see what happens with other languages:

Haskell (using the Glasgow Haskell Compiler):
[PHP]main = do
	print "Hello World!"[/PHP]

```
ghc helloworld.hs
```

Output:
a.out 594.3 KB (608589 bytes)

Holy crap.

Using any Lisp will give you sizes of MBs. PLT Scheme took 2.6 MB, SBCL took around 25 MB (!)... Stripping a Lisp image corrupts it.

I was unable to use Objective-C + GNUStep... it seems that there's a weird permissions issue in Debian with the GNUStep Makefiles...

---

