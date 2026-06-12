---
title: "Question about gdb"
date: 2010-05-09
forum: Programming Talk
---

### Post by silverdragon89 on 2010-05-09
I have a question about configuring gdb. I installed it with sudo apt-get install gdb I seem to be getting some problems. For a simple hello world program using printf, I get  

(gdb) b main
Breakpoint 1 at 0x80483ed: file test.c, line 5.
(gdb) run

Breakpoint 1, main (argc=1, argv=0xbffff4a4) at test.c:5
5       printf("Hello World\n");
(gdb) s
_IO_puts (str=0x80484c0 "Hello World") at ioputs.c:37
37    ioputs.c: No such file or directory.
    in ioputs.c
(gdb) bt
#0  _IO_puts (str=0x80484c0 "Hello World") at ioputs.c:37
#1  0x080483f9 in main (argc=1, argv=0xbffff4a4) at test.c:5

This happens for stuff like malloc or pretty much any library calls I make.

---

### Post by Bachstelze on 2010-05-09
Can you show us your code?

---

### Post by silverdragon89 on 2010-05-09
The code is simply:

#include <stdio.h>

int main(int argc, char *argv[])
{
   printf("Hello World\n");
   return 0;
}

It compiles and runs fine with gcc.

---

