---
title: "Assembler languages for Linux"
date: 2009-02-07
forum: Programming Talk
---

### Post by Jack Shankle on 2009-02-07
Hi Folks,
Thanks for any responses.
I am faced with the daunting task of switching from MASM32 to one
of the many Assembler languages for Linux. Most people will recommend
the one they are using but it might not be the best choice. I know all
about not wanting to learn something new just because it's better.
Let's see there is Nasm, Fasm, Jwasm, Wasm, Gas and I am sure there are many others. Are they usable on all the distros? I will be using Ubuntu.  
Are there forums for each language? Are there PDF manuals that can be downloaded? Which language is kept current and not outmoded? Who maintains the various languages and are they active? 
I sure there are many more questions that I should be asking but that is
all I can think of at the moment.

---

### Post by andrewc6l on 2009-02-07
I don't know what criteria you use for a good assembler, but at least on 8.04, /usr/bin/as is the GNU assembler, which will be available on all platforms that have GNU C (including Windows, if you have to go there), so it's probably the most portable. Also, it's guaranteed to work with gcc -S, whereas the others might not.

---

### Post by Tek-E on 2009-02-07
I am rather new to assembly and I am still in the pocess of working with it, but I installed NASM (I know its kinda outdated...at least the version I have is) on ubuntu and I havnt had any problems with it so far.

---

### Post by dburnett77 on 2009-02-07
> **Jack Shankle said:**
> Hi Folks,
Thanks for any responses.
I am faced with the daunting task of switching from MASM32 to one
of the many Assembler languages for Linux. Most people will recommend
the one they are using but it might not be the best choice. I know all
about not wanting to learn something new just because it's better.
Let's see there is Nasm, Fasm, Jwasm, Wasm, Gas and I am sure there are many others. Are they usable on all the distros? I will be using Ubuntu.  
Are there forums for each language? Are there PDF manuals that can be downloaded? Which language is kept current and not outmoded? Who maintains the various languages and are they active? 
I sure there are many more questions that I should be asking but that is
all I can think of at the moment.

[http://en.wikipedia.org/wiki/High_Level_Assembly](http://en.wikipedia.org/wiki/High_Level_Assembly)

hla is one I've heard of.  High-Level Assembly.  Supports many platforms.

---

### Post by jimi_hendrix on 2009-02-07
i've messed around with nasm...it has very good documentation

its the only one ive tried

---

### Post by happysmileman on 2009-02-07
GAS would probably be the most used, it comes with GCC so will be updated and work on all distros, as said above it'll work with gcc -S whereas I don't think any others will (at least not all the time).

---

### Post by Krupski on 2009-02-07
> **Jack Shankle said:**
> I am faced with the daunting task of switching from MASM32 to one
of the many Assembler languages for Linux.

REAL men program with toggle switches and ferrite core memory!

:)

---

### Post by Jack Shankle on 2009-02-07
I have not been able to find the as/gas or gnu compiler to download.
I assume these are the same thing and are the assembler language and NOT C.
I've seen a lot of very confusing things. They are not part of the Ubuntu
distribution.
Thanks for any clarification.

---

### Post by snova on 2009-02-07
First, there is GCC- a compiler suite for C, C++, Fortran, Ada, and countless more (well... not countless, but a lot!). They all use Gas as their backend, an assembler.

Gas is AT&T syntax. I believe there is a switch to make it accept Intel syntax, however.

Then there is Nasm, which has an Intel syntax.

I suggest Nasm; I find Intel syntax easier to read.

Chances are, you have GCC installed. And thus you also have Gas installed (GCC wouldn't work without it, after all). Nasm may or may not already be present.

---

### Post by happysmileman on 2009-02-07
> **Jack Shankle said:**
> I have not been able to find the as/gas or gnu compiler to download.
I assume these are the same thing and are the assembler language and NOT C.
I've seen a lot of very confusing things. They are not part of the Ubuntu
distribution.
Thanks for any clarification.

Install gcc and you will get it, it's included with the GCC compilers, but it's an assembler.
(AFAIK the reason for this is that GCC/G++ will first convert the C/C++ code to assembly, and then this assembler will build it, you can use gcc -S to convert your C code to assembly code in the right syntax for this assembler)

And yes it's not a C compiler, but don't know if there's a way to install it separately (at least not without building it yourself)

---

### Post by snova on 2009-02-07
> **happysmileman said:**
> Install gcc and you will get it, it's included with the GCC compilers, but it's an assembler.
(AFAIK the reason for this is that GCC/G++ will first convert the C/C++ code to assembly, and then this assembler will build it, you can use gcc -S to convert your C code to assembly code in the right syntax for this assembler)

Technically, what it does is leave off the last step, assembly.

> And yes it's not a C compiler, but don't know if there's a way to install it separately (at least not without building it yourself)

It's part of **binutils**, along with the linker, archive tool, and several other utilities.

---

### Post by Jack Shankle on 2009-02-07
Thanks guys for the guidance.
I understand that "Yasm" is an improved "Nasm".
Both are in the Ubuntu distribution.
I'm also interested in a flat Assembler. The other kind
should never have been written IMHO.
Wouldn't it be better to go that way? 
Think I'll give up on as/gas.
Be interested in your opinions.

---

### Post by snova on 2009-02-07
> **Jack Shankle said:**
> I understand that "Yasm" is an improved "Nasm". Both are in the Ubuntu distribution.

Then use it. :) Whatever suits you.

> I'm also interested in a flat Assembler. The other kind should never have been written IMHO.

What exactly is a "flat" assembler? And why would it be better?

I sure hope you aren't talking about one that spits out flat binaries, because such outputs are pretty much useless (unless you're doing something odd)...

---

### Post by Jack Shankle on 2009-02-07
It not what suits me as I am unfamiliar with both of them. It's what I picked up from reading and wished to verify it.

The old MASM worked with segments and was a royal pain to program. The
later MASM32 uses a flat structure and can address a much larger structure
and is a much better way of doing things. I was wondering if "Nasm" or "Yasm" was flat in it's structure?

---

### Post by snova on 2009-02-07
> **Jack Shankle said:**
> The old MASM worked with segments and was a royal pain to program. The later MASM32 uses a flat structure and can address a much larger structure and is a much better way of doing things. I was wondering if "Nasm" or "Yasm" was flat in it's structure?

Yes, as are all assemblers for Linux (I think).

I don't think it's so much a product of the assembler as it is of the OS. And Linux does not use segments very much.

---

### Post by eye208 on 2009-02-07
> **Jack Shankle said:**
> Most people will recommend
the one they are using but it might not be the best choice. I know all
about not wanting to learn something new just because it's better.
What makes one assembler better than another? They all take your input files and convert them to machine code, instruction by instruction. Unlike compilers, assemblers do not optimize your code in any way. The quality of the generated code will not be affected by the assembler you choose. And the language syntax is always the same, unless you change the target CPU.

The GNU compiler front end (gcc) identifies input files by their file name extensions. Files ending with .c will be passed on to the C compiler. Files ending with .s will be passed on to the assembler. It's just that simple.

---

### Post by Wybiral on 2009-02-07
> **eye208 said:**
> What makes one assembler better than another? They all take your input files and convert them to machine code, instruction by instruction. Unlike compilers, assemblers do not optimize your code in any way. The quality of the generated code will not be affected by the assembler you choose. And the language syntax is always the same, unless you change the target CPU.

Agreed. There's little debate between assemblers since the underlying processor uses the same mnemonics... Aside from syntax, the only real difference will be if the assembler supports some form of macros, but even then, the differences are trivial. If you're familiar with intel-syntax, use nasm/yasm/fasm, if you prefer at&t, use gas...

---

### Post by Sorivenul on 2009-02-07
I prefer Intel syntax and use [fasm]("http://www.flatassembler.net/"). I've also used nasm without problems. As has been stated, macro support will be about the largest, but still relatively trivial difference.

EDIT:
An interesting article from IBM on GAS vs. NASM in Linux:
[http://www.ibm.com/developerworks/library/l-gas-nasm.html](http://www.ibm.com/developerworks/library/l-gas-nasm.html)
An brief overview, yet far more in depth than one of us would reasonably post:
[http://webster.cs.ucr.edu/AsmTools/WhichAsm.html](http://webster.cs.ucr.edu/AsmTools/WhichAsm.html) - Note: this may be considered dated, but is still mostly applicable.

---

### Post by slavik on 2009-02-08
to expand a little on assemblers ...

yes, there is a difference, some assemblers will optimise things, others won't. assemblers are smart in the sense of know which instruction takes how long and can re-order them based on that.

as Sorivenul almost completely mentioned, there is also a syntax difference. there is the AT&T syntax which is what GAS understands and also the Intel syntax, which is what nasm understands. the syntax has to do with where l-values are placed and how addresses/registers are denoted.

---

### Post by eye208 on 2009-02-08
> **slavik said:**
> yes, there is a difference, some assemblers will optimise things, others won't. assemblers are smart in the sense of know which instruction takes how long and can re-order them based on that.
In my opinion these are not assemblers. They are compilers with an assembly-like syntax. The whole point of using assembly language is to have 100% control over the code that is generated, e.g. to implement self-modifying code etc.

> as Sorivenul almost completely mentioned, there is also a syntax difference. there is the AT&T syntax which is what GAS understands and also the Intel syntax, which is what nasm understands.
GAS understands both. I would recommend using Intel syntax only.

---

### Post by Jack Shankle on 2009-02-20
I would be interested on your opinions of two Assembly languages.
"jwasm" and "Sol_Asm. Sol_Asm looks to be a very powerful language.
It is my understanding that they both will work on Linux but does
that mean that they will work on Ubuntu?
Thank you for any info.

2% ubuntu working on 3%

---

### Post by snova on 2009-02-20
> **Jack Shankle said:**
> It is my understanding that they both will work on Linux but does that mean that they will work on Ubuntu?

Yes; Ubuntu is Linux.

---

### Post by slavik on 2009-02-21
> **eye208 said:**
> In my opinion these are not assemblers. They are compilers with an assembly-like syntax. The whole point of using assembly language is to have 100% control over the code that is generated, e.g. to implement self-modifying code etc.


GAS understands both. I would recommend using Intel syntax only.

fair argument on point 1. thanks for informing us on point 2.

---

