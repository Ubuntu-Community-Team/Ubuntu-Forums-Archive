---
title: "Alternative to GNU binutils??"
date: 2007-03-26
forum: Programming Talk
---

### Post by damvcoool on 2007-03-26
does it exist an alternative to the gnu binutilis??

---

### Post by Mr. C. on 2007-03-26
Like what?  What are you looking for ?  Binutils consists of many tools...

MrC

---

### Post by damvcoool on 2007-03-28
like the main utilities in binutils

ld - linker
as - assembler

---

### Post by Mr. C. on 2007-03-28
I know the names of what you are looking for.

What are your goals ?  There are many linkers, assemblers, etc.

Your question reads like "is there an alternative to four-wheel transportation".

Its your job to clarify specifically what you want, not mine to list all possibilities in time and space.

MrC

---

### Post by damvcoool on 2007-03-29
ohh ok, sorry :P, My goal is to make a system

uclibc
busybox
tcc
linux kernel

without using any GNU code on it.

---

### Post by Keffin on 2007-03-29
You could try looking through the FreeBSD package database for stuff, but their binutils packages seem to be GNU binutils based at least (I've only had a quick look).

Also if by "no GNU code" you mean no code using the GPL license (the only thing I can think of that makes any difference to anything) then you need to rethink your list because the linux kernel and busybox use the GPL (tcc and uclibc use the LGPL).

---

### Post by damvcoool on 2007-03-29
no gnu code means not written by the FSF or the GNU project. like uclibc and busybox, they come from other Project outside GNU. I realldy dont care about the license since i'm not going to retail this stuff nor i going to distribute it un less someone wants a copy :P but i need to make it work first but mostly i'm building it as a learning thing. and by building i mean uclibc, busybox, toybox, linux kernel,  tcc (compiler). 

Basically i'm missing the replacement for what binutils offers so i can build the system practically from scratch.

---

### Post by Wybiral on 2007-03-29
Whew... Good luck with that! Sounds painful...

---

### Post by damvcoool on 2007-03-30
> **Wybiral said:**
> Whew... Good luck with that! Sounds painful...

It is, speaciall for me because im just starting :P but I accept help :D

---

### Post by Mr. C. on 2007-03-30
I am completely baffled by what you are trying to accomplish.

You said you want to find alternatives to GNU/FSF/GPL utilities, but also say you want to build the system from scratch, but you also are requesting help to do it.  You're not going to sell it, will make it available upon request

If you are just trying to learn how to piece together a system, why do you prefer to avoid existing tools that happen to contain the GNU license?

Something is very fishy here.
MrC

---

### Post by simplyw00x on 2007-03-30
The only one of those that he actually says he's avoiding is GNU. He specifies several GPL-licensed tools as the foundation of his system. What;s so fishy here?

---

### Post by damvcoool on 2007-03-31
it is complicated, I want to avoid GNU and/or FSF code because when it is compiled it takes a lot of space and uses a lot of resources, i want somethin simple, easy to follow, and SMALL!! for example tcc (compiler) takes only 130k when compile with it self, busybox replaces most of the gnu utilities like Shell, ls, df, dd, su, sudo, awk. Toybox replaces make, and whatever make invoques (dont really know much about toybox), uclibc replaces gnu c library. I dont know if my point is clear but the only tool that i'm missing replacement is binutils core utilities which are ld (linker) and gas (assembler)

---

