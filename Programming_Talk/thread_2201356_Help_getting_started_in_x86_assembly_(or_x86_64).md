---
title: "Help getting started in x86 assembly (or x86_64)"
date: 2014-01-24
forum: Programming Talk
---

### Post by spencer the great on 2014-01-24
Hi, I was thinking of learning assembly language for x86 processors. I have a few questions, though, that I can't seem to find on Google.  What kind of knowledge/tools do I need for this? Also, through a few google searches, I learned that the x86_64 instruction set is just an extension of the x86 set.  Does that mean the code designed for x86 machines will work on x86_64? Lastly, is there any difference at all between amd64 and x86_64?

EDIT: Also, is there a particular assembler I should use? I was planning to use GNU binutils as, but I also stumbled upon NASM and I don't know if there are any differences.

---

### Post by Bachstelze on 2014-01-24
Study [this book]("http://csapp.cs.cmu.edu/").

But to answer your questions...

> **spencer the great said:**
> What kind of knowledge

See above.

> **spencer the great said:**
> tools

A text editor, an assembler and probably a compiler/linker as well. Just install build-essential, binutils, and your favourite text editor and assembler.

> **spencer the great said:**
> I learned that the x86_64 instruction set is just an extension of the x86 set.  Does that mean the code designed for x86 machines will work on x86_64?

Yes, although in some cases if you have a 64 bit OS, you need to install additional software to run 32 bit code. This is a limitation of the OS, not of the CPU.

> **spencer the great said:**
> Lastly, is there any difference at all between amd64 and x86_64?

No, in most cases they are just different names for the same thing.

> **spencer the great said:**
> EDIT: Also, is there a particular assembler I should use? I was planning to use GNU binutils as, but I also stumbled upon NASM and I don't know if there are any differences.

Picking an assembler, just like picking a desktop environment or a text editor, is a matter of personal preference. GNU as and NASM/YASM basically just use different syntaxes to do the same thing.

---

### Post by ofnuts on 2014-01-24
In addition to Bachstelze's answer: the more familiar you are with binary & hex notation, and bitwise manipulations the better. And you'll need a debugger. I rarely use debuggers for high-level languages but for ASM it's quite unavoidable, adding print statements in the code being rather cumbersome and having side effects (register usage...).

---

### Post by ssam on 2014-01-24
You might like
[http://gcc.godbolt.org/](http://gcc.godbolt.org/)
I lets you see the assembly output from C source. (you might want to add -masm=intel to the compiler options to see x86)

---

