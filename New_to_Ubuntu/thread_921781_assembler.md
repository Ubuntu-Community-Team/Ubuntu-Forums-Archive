---
title: "assembler"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by new Student on 2008-09-16
hi guys

sorry guys for bothering you again ( psst i did not search the web )

assembler or assembly compiler

i need a good assembler for a newbie in assembly language 

i mean an assembler that can assemble  hello world programs or something 

like that

any recommendations ? 

PS: i don't want you to recommend me to learn c++

---

### Post by DrMega on 2008-09-16
You didn't say what CPU (instruction set) you are interested in.

---

### Post by new Student on 2008-09-16
what is CPU (instruction set) ?

hmmmm i think i got the an idea i got intel P4 is that it ?

i think i need more education on assembly

---

### Post by DrMega on 2008-09-16
Basically, each type of process is only capable of running code that uses its own particular instruction set (unless it emulates another set).

If you write assembly language code it is usually because you want absolute control of a specific piece of hardware. I'm going back a few years now, but when I was a student (not so many years ago) the Motorola 68000 series of CPUs were still in common use, and the Intel 80x86 series (the Pentium ancestors) were also popular. You would write M68000 code for something that was to run on an M68000 processor, and you would write 80x86 code for stuff that was to run on the 80x86 series.

As for your 'Hello world' objective, that will depend on the target hardware too. If it is to run native on a PC, then you will need to learn about bios calls (unless you know how to get an address pointer to a pointer to a suitable library). Also, if it is going to run native (ie not in an emulator) then expect many unhandled crashes.

I'm not trying to put you off, good luck in your quest, but assembly language is very hardware specific so unless you are building a custom computer or microcontroller, you would find one of the higher level languages (which are not so hardware specific) more productive.

---

### Post by phidia on 2008-09-16
[This]("http://www.freebyte.com/programming/assembler/") might be a useful site to check out.

---

### Post by cb951303 on 2008-09-16
[http://nasm.sourceforge.net/](http://nasm.sourceforge.net/)
[http://www.flatassembler.net/](http://www.flatassembler.net/)

---

