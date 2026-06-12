---
title: "C shared library with inline asm on 64bit system"
date: 2012-05-27
forum: Packaging and Compiling Programs
---

### Post by ordine on 2012-05-27
hi,
just to understand how it works i'm triyng to create a C shared library with inline assembler on 64 bit system, but compiling it i have:

gcc -fPIC -Wall -g -c libhello.c
(it's OK, but in the next command there's an error)
gcc -g -shared -Wl,-soname,libhello.so.0 -o libhello.so.0.0 libhello.o -lc
relocation R_X86_64_32S against `.bss' can not be used when making a shared object; recompile with -fPIC

same problem with:
gcc -fPIC -g -shared -Wl,-soname,libhello.so.0 -o libhello.so.0.0 libhello.o -lc

and this is my libhello.c file:

static unsigned int cbr asm("rbxregistro");     
int hello(int numero) {
  numero++;
cbr=numero;
asm("mov rbxregistro,%ax");
}

and the problem is in relocation of 'rbxregistro' variable: asm("mov rbxregistro,%ax");

In 32bit system i found no problems; which way for 64bit?
thanks

---

### Post by MadCow108 on 2012-05-27
not sure why it works on 32 bit, probably related to the differences in pic code between i386 and amd64.

to fix it you need to use an address relative move, else you end up with position dependent code which does not work for shared libraries.
I think
```
asm("mov rbxregistro(%rip),%ax");
```
might do it, but my assembler skills really suck.

---

### Post by ordine on 2012-05-28
SOLVED!
non multa sed multum, 
benissimo, now it works perfectly
best regards
roberto

---

