---
title: "Assembly -  a few questions."
date: 2008-02-11
forum: Programming Talk
---

### Post by Senesence on 2008-02-11
I'm taking an assembly programming class this semester. The book we're using (kip irvine, 5th edition) is very heavily windows and MASM oriented, so I thought it would be a good idea to ask about the tools available under Linux for some assembly experimentation (I'd like to avoid booting into windows for all the general programs that don't require OS specific functions).

Now, I know about assemblers like GAS and NASM, but I also read something about being able to just use the GNU C compiler. Can anyone elaborate on that, and what the differences are compared to using GAS or NASM to "assemble" assembly code?

Also, about safety; From what I've read, assembly is very, very low-level, which means the programmer is allowed to do pretty much anything -> Does that mean that I could potentially mess things up to the point where I won't be able to reboot? I mean could I accidentally do something that would "break" a piece of hardware?

Or is the risk about the same as programming in C/C++.

Thanks.

---

### Post by lnostdal on 2008-02-11
take a look at [http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

programs written in asm run as normal processes under the OS - with the same restrictions as them .. there is nothing special about asm, it's just another language

..as always -- don't run software you do not trust as root

---

### Post by Wybiral on 2008-02-11
> **Senesence said:**
> I'm taking an assembly programming class this semester. The book we're using (kip irvine, 5th edition) is very heavily windows and MASM oriented, so I thought it would be a good idea to ask about the tools available under Linux for some assembly experimentation (I'd like to avoid booting into windows for all the general programs that don't require OS specific functions).

Since most pure assembly programs will be using system calls, it's going to be platform specific (unless you're using a higher-level assembly language).

> **Senesence said:**
> Now, I know about assemblers like GAS and NASM, but I also read something about being able to just use the GNU C compiler. Can anyone elaborate on that, and what the differences are compared to using GAS or NASM to "assemble" assembly code?

GCC uses GAS to assemble the code that it compiles. The only difference, really, between GAS and NASM are that NASM is intel syntax and GAS is at&t syntax. They have backwards operands :)

> **Senesence said:**
> Also, about safety; From what I've read, assembly is very, very low-level, which means the programmer is allowed to do pretty much anything -> Does that mean that I could potentially mess things up to the point where I won't be able to reboot? I mean could I accidentally do something that would "break" a piece of hardware?

Or is the risk about the same as programming in C/C++.

Thanks.

Unless you're programming in [real mode]("http://en.wikipedia.org/wiki/Real_mode"), you should be OK. Since you're running either Linux or Windows, you'll be in [protected mode]("http://en.wikipedia.org/wiki/Protected_mode"). Just don't mess around with any direct hardware communication that you aren't sure about. I'm sure they'll explain this to you in class.

---

### Post by rplantz on 2008-02-11
> **Senesence said:**
> I'm taking an assembly programming class this semester. The book we're using (kip irvine, 5th edition) is very heavily windows and MASM oriented, so I thought it would be a good idea to ask about the tools available under Linux for some assembly experimentation (I'd like to avoid booting into windows for all the general programs that don't require OS specific functions).

Now, I know about assemblers like GAS and NASM, but I also read something about being able to just use the GNU C compiler. Can anyone elaborate on that, and what the differences are compared to using GAS or NASM to "assemble" assembly code?

The biggest problem you would face is that Irvine (like almost all authors) uses Intel syntax and the GNU programming environment uses AT&T syntax. For example, to do a 32-bit copy from the A register to the B register in Intel syntax you write
```

mov ebx, eax

```
but in GAS you write
```

movl %eax, %ebx

```
Notice that the order of the operands is opposite. And GAS requires a "%" before each register name, and it requires the length of the data to be appended to the end of the instruction ("l" for "long").

This isn't a big deal for an assembly language programmer. I once did programming for two clients who used different machines and had to use both syntaxes almost every day. But I don't think that mixing them is a good idea while learning the material.

As for the relationship between gcc and gas, if you compile a C/C++ program with the -S (that's an upper-case S), gcc will produce a file with the ".s" extension that is its assembly language version of your C/C++ code. Of course, it uses AT&T syntax and there are no comments.

One of the neat things is that you can write in (gas) assembly language and assemble it. Then you can compile C/C++ code with the "-c" option to produce unlinked object files. Then you can use gcc to link all these object files (the ".o" ones) together, and gcc will even link in any functions you have called from the C standard library.

This is the way I taught the course. I'm working on a book that does it this way. Even better, my book uses the 64-bit mode.

> 
Also, about safety; From what I've read, assembly is very, very low-level, which means the programmer is allowed to do pretty much anything -> Does that mean that I could potentially mess things up to the point where I won't be able to reboot? I mean could I accidentally do something that would "break" a piece of hardware?

Or is the risk about the same as programming in C/C++.

Thanks.
Under Linux you have the same protection as with C/C++. The OS pretty much keeps you from doing bad things to it. I taught assembly language under Linux for six years and never had a student crash a machine.

---

