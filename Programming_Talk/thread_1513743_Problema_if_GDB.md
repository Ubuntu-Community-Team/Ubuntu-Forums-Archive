---
title: "Problema if GDB"
date: 2010-06-20
forum: Programming Talk
---

### Post by kiroth on 2010-06-20
HI folk.

With this program in C, for exemple:


#include <stdio.h>

int main() {

  printf(" TEST \n");
  
  return 0;
}

When I'm debbuging with GDB I receive this:

Temporary  breakpoint 1 at 0x400558: file test.c, line 5.
Starting program: /home/user/test 

Temporary breakpoint 1, main () at test.c:5
5      printf(" TEST \n");
(gdb) s
_IO_puts (str=0x40065c " TEST ") at ioputs.c:35
35    ioputs.c: File or  directory not found
    in ioputs.c
(gdb) s
37    in ioputs.c
(gdb) 



Any help pls?

---

### Post by Zugzwang on 2010-06-21
So you try stepping into printf, which does not work because the sources for that function are not installed. This is because there is normally no need to step into library functions. 

So, unless you are actually interesting in finding out how the "printf" function works, just skip over it using "n".

---

