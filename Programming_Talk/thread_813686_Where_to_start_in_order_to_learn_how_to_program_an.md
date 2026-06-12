---
title: "Where to start in order to learn how to program an Emulator?"
date: 2008-05-31
forum: Programming Talk
---

### Post by Ioky on 2008-05-31
I know that sound silly, but I really wonder how people even get start on writing an Emulator like for other thing such as N64, PSX, and even Dos.

It is really hard to get information on such topic online. Just hoping any one might able to give me a hand here. 

I am not saying I am smart enough to even do much thing, I just want to learn something about it. just so I can have a better understand.

---

### Post by bapoumba on 2008-05-31
Moved to Programming Talk.

---

### Post by Wybiral on 2008-05-31
You have to understand the assembly format that those architectures use, then write a virtual machine to emulate that on your target platform.

---

### Post by Sockerdrickan on 2008-05-31
Grab source code and check out how it's done, start with a NES emu perhaps?

---

### Post by lisati on 2008-05-31
Fr starters, you'll probably need to translate system calls for the "guest" OS into the equivalent for the "host" OS. A few years ago I got hold of an MS-DOS reference called "Ralph Brown's interrupt list", possibly from the "Programmer's Heaven" website, which might make for interesting reading.

---

### Post by NormR2 on 2008-05-31
If you've never written an emulator, I'd suggest starting with a simple one. Define your own machine and a language for it and write an emulator for that. For example, define an instruction set with operations like Add, subtract, compare, load, store and jump. Give the machine some registers, a current location register and a condition/result flag.
Each of those instructions have several flavors. For example for Add: add from a memory address, add from the add instruction itself, add from another register, add from memory addressed by a register.

The emulator would be a switch/case statement driven by the operation code. Each opcode would do some work that would change a register, memory and/or the condition/result flag and would change the current location register.
For ease of testing, add some special instructions to display (write to stdout) the contents of registers or memory.

Define a simple language to use these instructions, write a program using that language and feed it to the emulator and see what happens.

---

### Post by gamelord12 on 2009-09-02
I just found this thread from a Google search.  Even though I had a whole semester's class on computer architecture, I still need to re-read what you just said and think about it for a while.  This stuff is so complex, it's amazing it ever gets done.  For instance, how would you even begin to discover the assembly language for an NES?  I only know Intel assembly because it was provided to me, and that took weeks to learn.

---

### Post by stroyan on 2009-09-02
> **gamelord12 said:**
> I just found this thread from a Google search.  Even though I had a whole semester's class on computer architecture, I still need to re-read what you just said and think about it for a while.  This stuff is so complex, it's amazing it ever gets done.  For instance, how would you even begin to discover the assembly language for an NES?  I only know Intel assembly because it was provided to me, and that took weeks to learn.
You get very familiar with a system by digging around collectors' groups and assorted garages for original developer's documentation.
(Somebody had to design that system and the games for it.)
And then experiment with physical examples of the various system revisions to find out where the documentation was incorrect. ;-)
Or, unless the system is extremely obscure, you just keep on googling for the documentation that somebody else already found and put on the internet.
Your NES example would lead to [http://nesdev.parodius.com]("http://nesdev.parodius.com/#Docs") .

---

