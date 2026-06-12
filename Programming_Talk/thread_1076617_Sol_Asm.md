---
title: "Sol_Asm"
date: 2009-02-21
forum: Programming Talk
---

### Post by Jack Shankle on 2009-02-21
I've finally made up my mind on an Assembler for Ubuntu - Sol_Asm. If anyone
is familiar with it I could use some help with the following:
Quote from the author: in order to obtain a functional binary executable for your OS(Ubuntu) you will have to:
1) link the provided elf obj with your OS libc and obtain the executable:

                   sol_asm2_unix_elf.obj 

I'm very new to Ubuntu and have no idea if or where "libc" is located or
what the author is means.
Thanks for any help.

2% Ubuntu working on 3%

---

### Post by jimi_hendrix on 2009-02-21
ok...liking basically takes all the object files you provide the linker (ld) and creates an executable out of them

if you do gcc this.c -o this.obj -c; g++ that.cpp -o this.obj -c

and lets say that.cpp includes the header for the stuff in this.cpp

g++ and gcc just compiled the source, now when we link it: ld -o executable this.obj that.obj

it will become an executable

can someone else give a better example...i read up on this when i learned asm (the first time a couple years ago) but cant remember it all

---

### Post by Jack Shankle on 2009-02-21
Thank you much for responding but that went straight over my head.
Guide me to where I can read and I will do.

---

### Post by Frank Kotler on 2009-02-22
How 'bout the comments in the examples?

libc should be in /lib, but gcc knows where to find it. The obj_native example doesn't need libc, so just "ld -e _start -o myprog myprog.o".

Oh, wait! You're still trying to build sol_asm! Sorry. Try:

gcc -O2 -o sol_asm sol_asm2_unix_elf.obj -lc

Probably don't need the "-lc" but it shouldn't hurt. (Linux library names all start with "lib", but it's stripped off - if you've got /lib/libsomething.so, just "-lsomething" to tell gcc about it.) Add a "2" to the output name, if you want. You probably *do* want "-O2" (optimization) - gcc generates some remarkably dumb code without it.

Best,
Frank

---

