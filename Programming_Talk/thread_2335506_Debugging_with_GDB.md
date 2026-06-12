---
title: "Debugging with GDB"
date: 2016-08-29
forum: Programming Talk
---

### Post by kinbalight on 2016-08-29
Hi, I am taking a course and am trying to use the GDB and "step" through each line of the code.

However, when I come to the printf statements, GDB always gives the error message
"printf.c: No such file or directory"

This does not happen when I use the "next" function of GDB.

Could anyone point out to me what may be causing the error? The source code is included below for reference.

[COLOR=#006400]#include <stdio.h>[/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]void sample_function()[/COLOR]
[COLOR=#006400]{[/COLOR]
[COLOR=#006400]	int i = 0xFFFFFFFF;[/COLOR]
[COLOR=#006400]	char buffer[10];[/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]	printf("In sample_function(), i is stored at 0x%08x.\n", (unsigned int)&i);[/COLOR]
[COLOR=#006400]	printf("In sample_function(), buffer is stored at 0x%08x.\n", (unsigned int)&buffer);[/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]	printf("Value of i before calling gets(): 0x%08x\n", (unsigned int)i);[/COLOR]
[COLOR=#006400]	gets(buffer);[/COLOR]
[COLOR=#006400]	printf("Value of i after calling gets(): 0x%08x\n", (unsigned int)i);[/COLOR]
[COLOR=#006400]	return;[/COLOR]
[COLOR=#006400]}[/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]int main()[/COLOR]
[COLOR=#006400]{[/COLOR]
[COLOR=#006400]	int x;[/COLOR]
[COLOR=#006400]
[/COLOR]
[COLOR=#006400]	printf("In main(), x is stored at 0x%08x.\n", (unsigned int)&x);[/COLOR]
[COLOR=#006400]	sample_function();[/COLOR]
[COLOR=#006400]}[/COLOR]

---

### Post by Rocket2DMn on 2016-08-29
I suggest reading up on the difference between step and next.  In summary, next will continue to the next line in the file that you're currently debugging - any function calls (like printf) are run to completion without stopping.  They have their own source code.  When you step, it will try to step into the printf function code, but you don't have the sources available.  The sources are probably in a package like glibc-source, but the installed glibc is probably optimized anyway, so you don't get much out of it.

---

### Post by kinbalight on 2016-08-29
Hi, thanks for the reply.

Yup I understand that "step" goes through each instruction line by line and stops. This is the particular instruction I'm trying to run with gdb as my intention is to look at the register pointers at each phase of the code. With "next" I am unable to examine the registers point by point.

When you mention the printf source are in a package, could I download and install said package?

---

### Post by steeldriver on 2016-08-29
You would need to install the glibc source I think - and then also add the relevant source directory to the gdb search path

To illustrate, I added source repositories, then created a /usr/local/src dir and ran

```

sudo apt-get source glibc

```

which (on 16.04) produces a /usr/local/src/glibc-2.23/ directory. You should find the printf.c source file in a stdio-common subdirectory.

[NOTE: you could apt-get the source into a user-owned directory of your choice WITHOUT needing sudo - I just wanted to put it somewhere common]

Then given

```

$ cat hello.c
#include <stdio.h>

int main(void)
{
  printf("Hello world!\n");

  return 0;
}

$ gcc -g -fno-builtin hello.c

```

if we do

```

$ gdb a.out
GNU gdb (Ubuntu 7.11.1-0ubuntu1~16.04) 7.11.1
.
.
.
(gdb)
(gdb) list
1       #include <stdio.h>
2
3       int main(void)
4       {
5         printf("Hello world!\n");
6
7         return 0;
8       }
(gdb) b 5
Breakpoint 1 at 0x40052a: file hello.c, line 5.
(gdb) r
Starting program: /home/steeldriver/forums/a.out

Breakpoint 1, main () at hello.c:5
5         printf("Hello world!\n");
(gdb) s
__printf (format=0x4005c4 "Hello world!\n") at printf.c:28
**28      printf.c: No such file or directory.**

```

whereas if we first add the source dir

```

**(gdb) dir /usr/local/src/glibc-2.23/stdio-common/**
Source directories searched: /usr/local/src/glibc-2.23/stdio-common:$cdir:$cwd
(gdb) b 5
Breakpoint 1 at 0x40052a: file hello.c, line 5.
(gdb) r
Starting program: /home/steeldriver/forums/a.out

Breakpoint 1, main () at hello.c:5
5         printf("Hello world!\n");
[B](gdb) s
__printf (format=0x4005c4 "Hello world!\n") at printf.c:28
28      {
[/B](gdb)

```

---

