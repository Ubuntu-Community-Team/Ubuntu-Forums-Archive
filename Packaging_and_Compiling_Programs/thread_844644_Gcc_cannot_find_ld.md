---
title: "Gcc cannot find ld"
date: 2008-06-29
forum: Packaging and Compiling Programs
---

### Post by sam159 on 2008-06-29
When i try and compile a simple program ie "int main(void) { return 0; }" gcc returns :
```
$gcc -o test.o test.c
collect2: cannot find 'ld'
```
ld is installed 
```
$ ld
ld: no input files
$ whereis ld
ld: /usr/bin/ld /usr/share/man/man1/ld.1.gz
```
So i assume there is some problem with how collect2 is searching for it
Heres the output from "gcc -print-search-dirs"
```
install: /usr/lib/gcc/i486-linux-gnu/4.2.3/
programs: =../lib/gcc/i486-linux-gnu/4.2.3/:../lib/gcc/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/libexec/gcc/i486-linux-gnu/4.2.3/:/usr/libexec/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/:../i486-linux-gnu/bin/i486-linux-gnu/4.2.3/:../i486-linux-gnu/bin/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../i486-linux-gnu/bin/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../i486-linux-gnu/bin/
libraries: =../lib/gcc/i486-linux-gnu/4.2.3/:../lib/gcc/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/4.2.3/:../i486-linux-gnu/lib/i486-linux-gnu/4.2.3/:../i486-linux-gnu/lib/../lib/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../i486-linux-gnu/lib/i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../i486-linux-gnu/lib/../lib/:../lib/i486-linux-gnu/4.2.3/:../lib/../lib/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../i486-linux-gnu/4.2.3/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/:/lib/i486-linux-gnu/4.2.3/:/lib/../lib/:/usr/lib/i486-linux-gnu/4.2.3/:/usr/lib/../lib/:../i486-linux-gnu/lib/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../i486-linux-gnu/lib/:../lib/:/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../:/lib/:/usr/lib/
```

Anyone have a clue whats going on?

---

### Post by Genotrius on 2008-09-24
I have the same problem, except that where the output from gcc -print-search-dirs says "4.2.3" for you, it says "4.2.4" for me. 
Someone told me I could put on hardy-proposed and hardy-backports, and not have any negative effects. I guess they were wrong... Or right.

---

