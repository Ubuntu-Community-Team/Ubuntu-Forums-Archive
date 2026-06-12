---
title: "Why won't a C program compiles in Linux run on windows?"
date: 2009-12-24
forum: Programming Talk
---

### Post by mahela007 on 2009-12-24
I tried compiling a program under linux and running it under windows on the same machine (It's a dual boot setup). Why doesn't it work? Isn't the machine code generated on compiling the same for any operating system?
It was a very simple program of the 'hello world' type...

---

### Post by dwhitney67 on 2009-12-24
There are probably numerous reasons, not having to do with the machine code.  For starters, consider the C library on which your Linux app is dependent upon.  It is not available under Windoze.

If you want portability, then recompile your program under Windows.

---

### Post by Can+~ on 2009-12-24
Not exactly.

Believe or not, many of the things you're doing an a standard C produces different results, depending on the OS.

Pretty much all I/O depends on interrupt codes, which differ from OS to OS.

---

### Post by Majorix on 2009-12-24
Which tool did you use to build the .exe?

---

### Post by Quarg on 2009-12-24
Yeah, if you ever look at assembly language, any sort of communication with the user of the computer (such as printing out "helloworld") relies on interrupts. for example, printing helloworld  to the console means that a function opens writes to the STDOUT file, by putting a few things in registers that the OS will look for, and then calling an interrupt, which hands control to the OS, which then looks at your registers, sees that you want to write to a file with a descriptor of 1, (STDOUT always has this file descriptor), and sees a pointer to a string somewhere. this is with  a Linux, (UNIX is probably similar) OS. with windoze, it probably looks to completely different registers, and has a different interrupt code, and doesn't even write to a file. that's why no executable made for windows will run on linux, and vice versa. they are completely different platforms; the OS'es do things very differently.

---

### Post by snova on 2009-12-24
> **mahela007 said:**
> I tried compiling a program under linux and running it under windows on the same machine (It's a dual boot setup). Why doesn't it work? Isn't the machine code generated on compiling the same for any operating system?
It was a very simple program of the 'hello world' type...

The most basic reason is executable file formats. Linux uses ELF, and Windows uses PE. While it's possible to use these formats on other systems (ELF is relatively widespread), they're not native and require additional compatibility layers. Windows will not even view ELF files as valid executables, and this is probably the first issue to meet.

Then there may be incompatibilities introduced by compilers. GCC may use a different calling convention, mangling scheme, etc., than MSVC and other libraries on the system. These issues get in the way when trying to link code produced by different compilers.

If you use libraries specific to one platform, it becomes more difficult to run it on another, as this code must also be ported (or run natively, like Wine).

Interrupts are only relevant for the most basic syscalls, and not even then are they the only way to do it. Linux makes use of both interrupts and sysenter/sysexit, and Windows may use something else entirely. And syscalls, from my understanding, aren't usually used directly (I do not think GCC wil generate these) unless it is from hand-written asm, and even then there is little reason to.

The code itself will run, unless you compiled it for a different architecture. But the operating systems work very differently, and generally programs are very boring unless they somehow interface with the OS...

---

