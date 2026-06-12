---
title: "stdio.h and stdlib.h appear to be missing"
date: 2007-05-12
forum: Programming Talk
---

### Post by lostvicking on 2007-05-12
I was trying to do some (beginner) C programming on Fiesty and encounter prblems with my #include statements. So this is what happens:

Code:

#include <stdlib.h>
#include <stdio.h>

main() {
	char char_buffer;

	printf("\nType in a line, up to 80 characters, and ");
	printf("the computer will repeat\n");
	printf("it using getchar() and putchar().\n");
	
	while( (char_buffer = getchar() ) != '\n' ) {
		putchar(char_buffer);
	}
	
	printf("\n\nPlease type in another line. This time the ");
	printf("computer will use the \n");
	printf("functions getc() and putc(). \n");
	
	while ( (char_buffer = getc(stdin) ) != '\n') {
		putc(char_buffer, stdout);
}			

Compile command: 
 gcc -v -c  stream.c

Result:
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
 /usr/lib/gcc/i486-linux-gnu/4.1.2/cc1 -quiet -v stream.c -quiet -dumpbase stream.c -mtune=generic -auxbase stream -version -fstack-protector -fstack-protector -o /tmp/ccgkm74v.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.1.2/include
 /usr/include
End of search list.
GNU C version 4.1.2 (Ubuntu 4.1.2-0ubuntu4) (i486-linux-gnu)
        compiled by GNU C version 4.1.2 (Ubuntu 4.1.2-0ubuntu4).
GGC heuristics: --param ggc-min-expand=64 --param ggc-min-heapsize=64371
Compiler executable checksum: c0d954aeefbb96d795ff3f6b3b72ef51
stream.c:1:20: error: stdlib.h: No such file or directory
stream.c:2:19: error: stdio.h: No such file or directory
stream.c: In function ‘main’:
stream.c:7: warning: incompatible implicit declaration of built-in function ‘printf’
stream.c:19: error: ‘stdin’ undeclared (first use in this function)
stream.c:19: error: (Each undeclared identifier is reported only once
stream.c:19: error: for each function it appears in.)
stream.c:20: error: ‘stdout’ undeclared (first use in this function)
stream.c:21: error: expected declaration or statement at end of input


I looked in /usr/lib/gcc/i486-linux-gnu and the stdio and stdlib headers really don't appear there. Kinda stumped on what to do

Please help! :P

---

### Post by lostvicking on 2007-05-12
After searching the forum for a bit found the following thread that solves this. Apparently GCC does not install properly sometimes, or I was stupid when installing it, either way: [http://ubuntuforums.org/showthread.php?p=2642484#post2642484](http://ubuntuforums.org/showthread.php?p=2642484#post2642484)

---

### Post by bukwirm on 2007-05-12
Did you install the build-essential package?

---

### Post by WW on 2007-05-12
> **lostvicking said:**
>  Apparently GCC does not install properly sometimes, or I was stupid when installing it, ...
I suspect neither is the case.  Most of us are suprised to find that the C compiler is not installed by default--I know I was.  These forums are riddled with questions exactly like yours. So no, you are not stupid. :)

I don't think it is correct to say that "GCC does not install properly sometimes."  You have to be aware that "the" C compiler  is actually split into two packages.  The actual compiler (gcc) is packaged separately from the C libraries and header files (libc6-dev). To compile a typical C program, you must install both of these packages.  A frequent source of confusion is installing just **gcc** without **libc6-dev**.  This gives you the compiler, but none of the standard header files.

There is a "meta-package" called **build-essential** that depends on these packages, along with **g++**, **make** and **dpkg-dev**.  So a quick way to get the core C/C++ compiler and libraries is to give the command
```

$ sudo apt-get install build-essential

```
(or use Synaptic to install build-essential).

---

### Post by Novakane on 2007-05-13
> **WW said:**
> I suspect neither is the case.  Most of us are suprised to find that the C compiler is not installed by default--I know I was.  These forums are riddled with questions exactly like yours. So no, you are not stupid. :)

I don't think it is correct to say that "GCC does not install properly sometimes."  You have to be aware that "the" C compiler  is actually split into two packages.  The actual compiler (gcc) is packaged separately from the C libraries and header files (libc6-dev). To compile a typical C program, you must install both of these packages.  A frequent source of confusion is installing just **gcc** without **libc6-dev**.  This gives you the compiler, but none of the standard header files.

There is a "meta-package" called **build-essential** that depends on these packages, along with **g++**, **make** and **dpkg-dev**.  So a quick way to get the core C/C++ compiler and libraries is to give the command
```

$ sudo apt-get install build-essential

```
(or use Synaptic to install build-essential).

Thanks. I needed to know that, too. \\:D/

---

### Post by csimoes on 2007-10-29
Thanks for posting this.  I had trouble finding the right package name until this post. :)

---

### Post by Wybiral on 2007-10-29
This is a _really_ common problem with new developers to Ubuntu. Hopefully I'm not the only one who thinks the package name should be changed or it should be posted somewhere (but realistically, GCC should be fully installed by default).

---

