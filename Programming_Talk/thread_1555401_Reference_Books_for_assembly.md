---
title: "Reference Books for assembly"
date: 2010-08-18
forum: Programming Talk
---

### Post by Searock on 2010-08-18
Hi,
 
I am currently learning assembly language, but I don't know which books should I refer for Intel Architecture.
 
I have tried searching for some books but their syntax is sligtly different.
 
I am using IA32build for building programs
 
Here's a sample code.
 
```

.intel_syntax noprefix
 
.include "console.i"
 
.text
 
     display: .asciz "Hello World !"
 
_entry:
 
     Prompt display
 
.global _entry
 
.end

```

---

### Post by Bachstelze on 2010-08-18
> **Searock said:**
> 
I am currently learning assembly language, but I don't know which books should I refer for Intel Architecture.

[http://www.intel.com/products/processor/manuals/](http://www.intel.com/products/processor/manuals/)
 
Seriously, though, why would you want to write a program from scratch in IA32 assembly? It only makes sense for embedded devices, and those don't use IA32.

---

### Post by lordhaworth on 2010-08-18
See this thread:
[http://ubuntuforums.org/showthread.php?t=1554651&page=2](http://ubuntuforums.org/showthread.php?t=1554651&page=2)

My post in this thread was the following if you are definitely interested in a textbook:

> 
Hi,

For a comprehensive look at assembly - try "The Art of Computer Programming" By Donald Knuth. Its basically a book of algorithms using a hypothetical assembly code "MIX". 

It is certainly comprehensive but also guides the reader into the assembly code gently. I would recommend it, but you would be hard pressed to read the whole thing "as a book" - it is best to pick and choose what you would like to look at once you have been through the introduction to MIX


---

### Post by lordhaworth on 2010-08-18
Sorry, I didnt realise you were looking for something specific - but that thread above is worth looking at anyway

---

### Post by Searock on 2010-08-19
> **Bachstelze said:**
> [http://www.intel.com/products/processor/manuals/](http://www.intel.com/products/processor/manuals/)
 
Seriously, though, why would you want to write a program from scratch in IA32 assembly? It only makes sense for embedded devices, and those don't use IA32.
 
 
So what should I use instead of Ia32build, the whole thing is going above my head. I see different instruction set everywere on the internet.
 
I am using Intel x86 architecture, but the syntax I see in the intel's site is different.
Can you guide me to a good assembler ?
 
@lordhaworth Thank you I'll give it a try.

---

### Post by Bachstelze on 2010-08-19
> **Searock said:**
> So what should I use instead of Ia32build, the whole thing is going above my head. I see different instruction set everywere on the internet.
 
I am using Intel x86 architecture, but the syntax I see in the intel's site is different.
Can you guide me to a good assembler ?
 
@lordhaworth Thank you I'll give it a try.

yasm/nasm are good assemblers, but as I said, no one uses them to write whole programs, just single functions that need ASM optimizations.  If you really want to write a program from scratch  in assembly, then IA32Build is okay, but it's really a waste of your time IMO.

---

### Post by Searock on 2010-08-19
> **Bachstelze said:**
> yasm/nasm are good assemblers, but as I said, no one uses them to write whole programs, just single functions that need ASM optimizations. If you really want to write a program from scratch in assembly, then IA32Build is okay, but it's really a waste of your time IMO.
 
I am not going to write programs in assembly language. We have a module of Assembly language in our college, and my professor says that assembly language is not used much, but is used in scenearios where speed is really important and thanks for the advice. Is there any book or atleast tutorials which have examples of sourcecode assembled in ia32build ? I want to learn more about it. Thanks again.

---

### Post by Bachstelze on 2010-08-19
> **Searock said:**
> I am not going to write programs in assembly language. We have a module of Assembly language in our college, and my professor says that assembly language is not used much, but is used in scenearios where speed is really important

That is true.  However, this requires a different approach.  Typically, you would write your entire program in C, then generate the assembly code for the function you need to optimize.  For example, for an iterative factorial:

```
firas@tsukino ~ % cat fact.c 
int fact(int n)
{
    int i, f=1;
    for(i=1; i <= n; i++)
        f *= i;
    return n;
}

firas@tsukino ~ % gcc -S fact.c 
firas@tsukino ~ % cat fact.s 
	.text
.globl _fact
_fact:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$24, %esp
	movl	$1, -16(%ebp)
	movl	$1, -12(%ebp)
	jmp	L2
L3:
	movl	-16(%ebp), %eax
	imull	-12(%ebp), %eax
	movl	%eax, -16(%ebp)
	incl	-12(%ebp)
L2:
	movl	-12(%ebp), %eax
	cmpl	8(%ebp), %eax
	jle	L3
	movl	8(%ebp), %eax
	leave
	ret
	.subsections_via_symbols

```

You will have the "backbone" of your function, and then you can start optimizing it as needed, by editing the assembly code.

> Is there any book or atleast tutorials which have examples of sourcecode assembled in ia32build ?

Probably, but I don't know any (it's been a while since I last touched IA32Build).  Try asking your professor (if IA32Build is required for your course, he should be able to suggest some material about it).

---

### Post by Searock on 2010-08-19
> **Bachstelze said:**
> Typically, you would write your entire program in C, then generate the assembly code for the function you need to optimize. For example, for an iterative factorial.
 
You will have the "backbone" of your function, and then you can start optimizing it as needed, by editing the assembly code.
 
Wow, my professor never told me about these technique. You are a real genius.
 
> **Bachstelze said:**
> 
Probably, but I don't know any (it's been a while since I last touched IA32Build). Try asking your professor (if IA32Build is required for your course, he should be able to suggest some material about it). 

 
I think that's the only option left.
 
Thanks a lot. :smile:

---

