---
title: "Unable to run 32 bit assembly programs on 64 bit ubuntu Nasm / ld"
date: 2013-01-08
forum: Packaging and Compiling Programs
---

### Post by nomudkipz on 2013-01-08
I am on Ubuntu 12.10 64 bit.

I am trying to compile and run a simple hello world program with nasm. The program is 32 bit and I want to run it in 32 bit mode under my 64 bit system. I believe I have all compatibility libraries installed.

I try these commands.

```
$ nasm -f elf -g -F stabs easyprint.asm
$ ld -o easyprint easyprint.o
ld: i386 architecture of input file `easyprint.o' is incompatible with i386:x86-64 output
```Of course, I can compile the assembly program as 64 bit and it works.

```
$ nasm -f elf64 -g -F stabs easyprint.asm
$ ld -o easyprint easyprint.o
$ ./easyprint 
The quick brown fox jumps over the lazy dog.
```But I would rather run it in 32 bit mode. I know you can compile it for 32 mode with gcc -m32, but I don't want to use GCC to compile it and I don't need access to any of the C functions.

I know this problem has probably been asked a million times, but for some reason hours of googling haven't helped me. Thanks in advance.

---

### Post by MadCow108 on 2013-01-09
you need to add 
-m elf_i386

the the ld call
you need to have a 32 bit linker available (libc6:i386 in newer ubuntus)

---

