---
title: "What assembly language in GCC giving me?"
date: 2009-11-05
forum: Programming Talk
---

### Post by Renée Jade on 2009-11-05
G'day all,

Ok. I'm a C programmer (well, learning to be) and lately I've taken to reading quite a bit of my compiled code so that I can better understand C and assembly language and computer programming in general. But there are some things in the asm that I do not get. I would happily look these things up but I don't really know where to start. What I need to know is the name of the language of the code produced when I compile C code with GCC on my AMD Turion 64 machine running 32bit Linux. And is there anything else I should know about it so that I can teach it to myself properly? This sounds like a bit of a silly question but I really don't know where else to start. Everyone I've talked to has said "oh, that must be x86", but I'm not sure if they're right.

Cheers for any help.

---

### Post by Renée Jade on 2009-11-05
Doh! I misspelled the subject line.

---

### Post by howlingmadhowie on 2009-11-05
> **Renée Jade said:**
> G'day all,

Ok. I'm a C programmer (well, learning to be) and lately I've taken to reading quite a bit of my compiled code so that I can better understand C and assembly language and computer programming in general. But there are some things in the asm that I do not get. I would happily look these things up but I don't really know where to start. What I need to know is the name of the language of the code produced when I compile C code with GCC on my AMD Turion 64 machine running 32bit Linux. And is there anything else I should know about it so that I can teach it to myself properly? This sounds like a bit of a silly question but I really don't know where else to start. Everyone I've talked to has said "oh, that must be x86", but I'm not sure if they're right.

Cheers for any help.

if you've got the 32-bit version of ubuntu installed, gcc will produce code for i586.  try compiling with the -S tag, then you'll be able to see the assembly code.  a good guide to i586 assembly is the book "Programming from the ground up".  it can be downloaded [here: http://mirrors.zerg.biz/nongnu/pgubook/]("http://mirrors.zerg.biz/nongnu/pgubook/")

---

### Post by Renée Jade on 2009-11-05
> **howlingmadhowie said:**
> if you've got the 32-bit version of ubuntu installed, gcc will produce code for i586.  try compiling with the -S tag, then you'll be able to see the assembly code.  a good guide to i586 assembly is the book "Programming from the ground up".  it can be downloaded [here: http://mirrors.zerg.biz/nongnu/pgubook/]("http://mirrors.zerg.biz/nongnu/pgubook/")

:S I can see the assembly code. How else could I be reading it? I just need to know what it's called. Thanks though.

---

### Post by Renée Jade on 2009-11-05
> **howlingmadhowie said:**
> if you've got the 32-bit version of ubuntu installed, gcc will produce code for i586.  try compiling with the -S tag, then you'll be able to see the assembly code.  a good guide to i586 assembly is the book "Programming from the ground up".  it can be downloaded [here: http://mirrors.zerg.biz/nongnu/pgubook/]("http://mirrors.zerg.biz/nongnu/pgubook/")

:O This book looks great! Thanks man. :D

---

### Post by johnl on 2009-11-05
The code produced by GCC for GAS (the GNU Assember) uses AT&T syntax.  This is different from the Intel syntax used by other assemblers such as NASM, etc.

AT&T syntax looks like this:

movl %eax, %ebx # move eax to ebx

Intel syntax looks like this:

mov ebx, eax ; mov eax to ebx

Note that the order of the operands are swapped, and AT&T specifies the size of the operands (l) at the end of the mov instruction.

[This website](http://www.imada.sdu.dk/Courses/DM18/Litteratur/IntelnATT.htm) has a quick intro to the differences between the two.

---

### Post by Renée Jade on 2009-11-05
> **johnl said:**
> The code produced by GCC for GAS (the GNU Assember) uses AT&T syntax.  This is different from the Intel syntax used by other assemblers such as NASM, etc.

AT&T syntax looks like this:

movl %eax, %ebx # move eax to ebx

Intel syntax looks like this:

mov ebx, eax ; mov eax to ebx

Note that the order of the operands are swapped, and AT&T specifies the size of the operands (l) at the end of the mov instruction.

[This website]("http://www.imada.sdu.dk/Courses/DM18/Litteratur/IntelnATT.htm") has a quick intro to the differences between the two.

Haha. I had already worked out the thing with the *"l"* and the order of args. This was how I knew that all the "oh, it's x86" people were wrong. However, when I'm a first year programmer and I'm talking to electronics/computer science graduates, I don't like to shout "wrong!" unless I'm 101% sure :P. Cheers mate! :)

---

### Post by grayrainbow on 2009-11-05
Opcode+debugger(disassembling capable)

---

### Post by Renée Jade on 2009-11-05
Off-topic @johnl: Long John?

---

### Post by jabl on 2009-11-05
> **Renée Jade said:**
> Haha. I had already worked out the thing with the *"l"* and the order of args. This was how I knew that all the "oh, it's x86" people were wrong. 

Well, depends on what they mean, I suppose. If by "it's x86" they specifically mean the Intel syntax used by, say, Microsoft, sure. But the CPU itself doesn't have "AT&T" and "Intel" modes, when the assembler generates the object file, it's going to generate identical code. AT&T and Intel are just different ways of representing the same thing, as you surely have realized.

As an aside, the GNU assembler also understands the Intel syntax, ".intel_syntax" selects Intel mode.

---

### Post by mmix on 2009-11-05
Computer Systems: A Programmer's Perspective (CS:APP) 

[http://csapp.cs.cmu.edu/](http://csapp.cs.cmu.edu/)

---

