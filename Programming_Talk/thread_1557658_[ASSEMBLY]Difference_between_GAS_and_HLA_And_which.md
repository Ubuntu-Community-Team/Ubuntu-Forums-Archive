---
title: "[ASSEMBLY]Difference between GAS and HLA? And which is best to start with [ASSEMBLY]"
date: 2010-08-21
forum: Programming Talk
---

### Post by P-Geist on 2010-08-21
Hey guys and gals.

Im new to assembly and want to make a very basic OS later once i know a bit of assembly. So i went to the stickied thread on starting programming and went to the assembly part in which i found these two headings GAS and HLA, now i doubt that HLA stands for 'Hot Lesbian Action' i know it stands for 'High Level Assembly' and GAS stands for another thing, but which should i choose to start with and what resources are there other than the ones posted in the above mentioned thread?

Thanks Ubuntu Forums,
P-Geist

---

### Post by xb12x on 2010-08-21
Well since nobody has replied to your question yet, I'll add my opinion for what it's worth.

If you are going to learn assembly coding learn the Intel syntax. Most of the assembly code in the world uses the Intel syntax.

Previously GAS (the Gnu Assembler) used only the AT&T syntax for the x86/x86-64 CPU's. The latest version of GAS now supports the Intel syntax via the .intel_syntax directive.

However, my favorite assembler for Linux based projects is NASM. For me it is much more intuitive and straight forward than GAS, has much better support, examples, etc. An added benefit of using NASM is that your code could be easily made to assemble using MASM (Microsoft's assembler for DOS/Windows, etc). You can install it from Ubuntu's Synaptic Package Manager. 

Anyone that writes any assembly professionally will almost _always_ use Intel syntax. Anything not written in Intel syntax is the exception that proves the rule.

---

### Post by P-Geist on 2010-08-21
Thanks, that was a very detailed explanation. But still my question remains un-answered. I am using NASM, but the tutorials here are for either GAS or HLA. Which would be more appropriate for a NASM user?

P-Geist.

---

### Post by xb12x on 2010-08-21
If you want to learn a "high level assembler" learn 'C'.

Seriously, HLA is one of those oddball things you can find on the Internet that has no real practical use in everyday life. It's like learning Esperanto instead of Spanish, German, French, or English.

---

### Post by P-Geist on 2010-08-21
So what your saying is learn C. Which i am doing yes thanks. But do you also mean that i should learn HLA?

---

### Post by lisati on 2010-08-21
<mumble>While "C" might be considered by some to be low level language it's not really the same as assembler. 

(That feels better, having gotten that off my mind.)

---

### Post by xb12x on 2010-08-21
> **lisati said:**
> <mumble>While "C" might be considered by some to be low level language it's not really the same as assembler.

I'm sorry lisati. I didn't mean to offend you.

---

### Post by lisati on 2010-08-21
> **xb12x said:**
> I'm sorry lisati. I didn't mean to offend you.

No offense taken. I was thinking of something I'd read in another thread and probably should not have bothered intruding here.

---

### Post by texaswriter on 2010-08-22
Lol, I hate how everybody always slams assembly. This comes from a person learning C# with Mono Develop, which is pretty fairly abstracted.. But still, as languages get further and further abstracted [or whatevver you wanna call it, oh sorry, *ducks* "object oriented"], you need more and more programmers who can write the lower level code that you need to support this abstraction. Someone has to have the brains to make the abstraction actually work and be efficient. 

So quit picking on people who are trying to do assembly!!! 

:lolflag:

---

### Post by P-Geist on 2010-08-22
So i guess this thread was very much unwelcomed. C here i come and then Asm here i come. Thanks.

---

### Post by nvteighen on 2010-08-22
HLA is a weird hybrid with no clear reason to exist... Usually, either you need ASM for very very low-level stuff (bootloaders, drivers, kernels...) or something else for any higher level.

As said, GAS is an implementation and Assembly dialect... NASM, MASM are others. I prefer NASM because Intel syntax is clearer and more to my taste, but if you want to seriously learn ASM, learn both AT&T and Intel... For example, if you're interested in learning how gcc does stuff and you want to take a look at some "gcc -S" output, you'll need to know GAS... because that's what gcc uses.

Actually, besides a few subtle issues, GAS and NASM aren't that different. The most important differences are, for example, some metaprogramming features designed to make coding faster... but not actually related to how the code will work... It's fairly straightforward to translate GAS code into working NASM code and viceversa.

---

### Post by texaswriter on 2010-08-22
For all the rhetoric, here is an actual page that compares actual features, instead of generally saying one is <insert opinionated attribution here> because of <insert esoteric statements here>. 

[http://webster.cs.ucr.edu/AsmTools/WhichAsm.html](http://webster.cs.ucr.edu/AsmTools/WhichAsm.html)

An actual comparison of features and fair treatment of most. Some of the treatment of 16 bit assembly may be more or less accurate in relation to Linux, but that's irrelevant to overall picture. 

Here is a table quoted from the above website as an example, comparing certain high level features of *assembly*. Oh, also, just for those who brought in C, and always whenever assembly is brought up, it's a logical fallacy to bring something else up when talking about NOT that thing. In fact, it's called a red herring. We are talking about X, do not bring up Y. Y is not X, therefore it is not relevant as a substitute for X. 

The OP speaks about assembly. Assembly != C. Discussion of C, if you really want, can be taken to another thread, called " your own thread". 

[[URL=http://s210.photobucket.com/albums/bb118/coldestiniowa/screenshots/?action=view&current=ASMTable.jpg][IMG]http://i210.photobucket.com/albums/bb118/coldestiniowa/screenshots/th_ASMTable.jpg[/IMG]]("http://i210.photobucket.com/albums/bb118/coldestiniowa/screenshots/ASMTable.jpg")[/URL]

---

