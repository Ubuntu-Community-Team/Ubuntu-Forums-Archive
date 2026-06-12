---
title: "Assembler Warning"
date: 2006-01-27
forum: Programming Talk
---

### Post by bkv2k on 2006-01-27
I just put an AMD64-based motherboard in my machine and loaded ubuntu. It went unbelievably well. I loaded NASM and tried a HelloWorld program using the following:

nasm -f elf hello.asm

Assembled just fine.

g++ -Wall -s -nostartfiles hello.o

Linked just fine giving a.out and this warning:

warning: i386 architecture of input file 'hello.o' is incompatible with i38686-64

a.out runs as expected. Is there something I should be doing that I'm not when I assemble/link? And, is using gcc/g++ the way to link assembler files?

Thank for the help!

---

### Post by Lord Illidan on 2006-01-27
nasm is an x86 assembler, that is why it gives you the warning. You need a 64 bit assembler. 

Try looking at this page for some help : [http://www.x86-64.org/documentation/assembly](http://www.x86-64.org/documentation/assembly)

---

### Post by bkv2k on 2006-01-28
Thanks!  I'll give this a try.

---

