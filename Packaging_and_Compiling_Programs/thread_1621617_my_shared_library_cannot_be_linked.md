---
title: "my shared library cannot be linked"
date: 2010-11-14
forum: Packaging and Compiling Programs
---

### Post by susiriss on 2010-11-14
Hi All,
          I am writing my first shared library and compiled a simple library with single function and issued the following commands to compile it.

```
gcc -Wall -fPIC t1.c -c
```

t1.c is my library source.

```
gcc -Wall -shared -fPIC -Wl,-soname,libtest.so.1 -o libtest.so.1.0 t1.o

```
creates my library and create the symlinks. 

```
ln -s libtest.so.1.0 libtest.so
```

Then I issue ldconfig to set the path for my library.

```
ldconfig -nv .
```

which gives me an output like this which I guess, is an indication of success.

```
.:
	libtest.so.1 -> libtest.so.1.0 (changed)
```

```
gcc -Wall prog.c -ltest -L. -o exe
```
compiles my test program. But when I try to execute "exe", it gives me an error like this.

```
./exe: error while loading shared libraries: libtest.so.1: cannot open shared object file: No such file or directory
```

These are the steps given in all tutorials I've found, so wondering what went wrong. I'm running **Ubuntu 10.04 (64-bit), with kernel 2.6.35.7,** in case those matters. Please give me a clue to find the issue.

thanks.

---

### Post by susiriss on 2010-11-14
when I ran ldd on "exe", the output is like this.

        linux-vdso.so.1 =>  (0x00007fffc3d2e000)
	libtest.so.1 => not found
	libc.so.6 => /lib/libc.so.6 (0x00007f5d6a41b000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f5d6a7bc000)

---

### Post by SevenMachines on 2010-11-14
Can you post source code?

Do you get something like
> warning: implicit declaration of function ‘something’

when you compile your test program?

Maybe you've forgot to include your library header in your test program code?

Just guesses, if you post code it should be more obvious

---

### Post by susiriss on 2010-11-14
Hi SevenMachines, thanks for replying below is the source code for the lib and the program. I don't use a header file.

t1.c (library)
```
#include <stdio.h>

void hellolib(char* name)
{
    printf("Hello %s\n", name);
}
```

and the main program is this

```
extern void hellolib(char* name);

int main(void)
{
    hellolib("sampath");
    return 0;
}
```
~

---

### Post by SevenMachines on 2010-11-14
are you remembering to add the directory to the library path when running?
> LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./exe

---

### Post by susiriss on 2010-11-14
No, I don't set the LD_LIBRARY_PATH, but instead I run ldconfig. That would be enough, isn't it ?

---

### Post by susiriss on 2010-11-15
> **susiriss said:**
> No, I don't set the LD_LIBRARY_PATH, but instead I run ldconfig. That would be enough, isn't it ?

Ohh.. this work after I set this variable. The tutorial I read tells that either the ldconfig or LD_LIBRARY_PATH would work. But that seems false..

anyway.. thanks SevenMachines, for your kind help !!

---

