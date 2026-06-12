---
title: "gcc assembler"
date: 2009-07-14
forum: Programming Talk
---

### Post by sidious1741 on 2009-07-14
I not a very good programmer, but I wish to become better.  I want to learn more about how low level stuff works.  I'd like to look at assembly but I don't know which assembler to use.  I decided to try gcc's assembler but I've looked for quite some time and I can't find out what gcc uses.  Any suggestions on a different assembler or a name for gcc's assembler?

---

### Post by aesis05401 on 2009-07-14
> **sidious1741 said:**
> I not a very good programmer, but I wish to become better.  I want to learn more about how low level stuff works.  I'd like to look at assembly but I don't know which assembler to use.  I decided to try gcc's assembler but I've looked for quite some time and I can't find out what gcc uses.  Any suggestions on a different assembler or a name for gcc's assembler?

Hello, 

May I suggest that a solid book on algorithms may serve your purpose in a more immediate fashion, and may have a broader impact on your programming abilities than actually learning assembly language.  

I am sitting here staring at a fairly good book on the subject - 'Introduction to Algorithms Second Edition.'  

If that does not float your boat then a solid book on design patterns also seems to do wonders for inexperienced programmers.  

At worst, there is always the 'Code Complete' material from MS.  I read the second edition (I think that was the edition) and found the material to be kind of redundant, but someone without experience with program design and refactoring would probably benefit immensly from the tips in that book. 

Anyhow, a low level understanding of what a computer *should* be doing may be more important that an understanding of an actual low level language.  And an understanding of successful design patterns will help you no matter what language you are using.

Best of luck.

---

### Post by Thesuperchang on 2009-07-15
The assembler that comes packaged with gcc is designed to assemble the machine code that is churned out of either cc1 and cc. Given the likely hood of code error, AS has minimal debugging assistance and lacks a preprocessor(No commenting). To invoke the GNU assembler:

[PHP]as input.s -o output[/PHP]

If you are looking for an assembler with a preprocessor, I strongly recommend Flat Assembler. I've used flat assembler a few times, however I do try to avoid x86 assembly whenever possible.
[http://flatassembler.net/docs.php?article=manual]("http://flatassembler.net/docs.php?article=manual")

Your also probably going to need a reference manual for all the x86 instructions.
[http://ref.x86asm.net/coder32.html]("http://ref.x86asm.net/coder32.html")

---

### Post by rplantz on 2009-07-15
> **sidious1741 said:**
> I not a very good programmer, but I wish to become better.  I want to learn more about how low level stuff works.  I'd like to look at assembly but I don't know which assembler to use.  I decided to try gcc's assembler but I've looked for quite some time and I can't find out what gcc uses.  Any suggestions on a different assembler or a name for gcc's assembler?

The name of the assembler is "as". Try "info as" to learn about it.

---

### Post by sidious1741 on 2009-07-15
Is learning assembly really a way to learn computer architecture.  I became discouraged to see the assembly of

```
int main()
{
  return 0;
}
```

which is

```
	.file	"asmex.c"
	.text
.globl main
	.type	main, @function
main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	movl	$0, %eax
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu 4.3.3-5ubuntu4) 4.3.3"
	.section	.note.GNU-stack,"",@progbits
```

Is there's a better way to learn about computer architecture (Specifically what C++ programmers should know.  I don't care about how a processor works.)

---

### Post by lisati on 2009-07-15
> **sidious1741 said:**
> Is learning assembly really a way to learn computer architecture.  I became discouraged to see the assembly of

```
int main()
{
  return 0;
}
```

which is

```
	.file	"asmex.c"
	.text
.globl main
	.type	main, @function
main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	movl	$0, %eax
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu 4.3.3-5ubuntu4) 4.3.3"
	.section	.note.GNU-stack,"",@progbits
```

Is there's a better way to learn about computer architecture (Specifically what C++ programmers should know.  I don't care about how a processor works.)

Compilers often add some "extra" stuff which is relevant to debuggers and other tools for the language and/or platform they're designed for, and that might not mean much to the casual programmer. You might find it easier and more useful if you browse the code samples at [http://www.programmersheaven.com/](http://www.programmersheaven.com/) or find a good book.

---

### Post by Thesuperchang on 2009-07-15
[PHP]	.file	"asmex.c"
	.text
.globl main
	.type	main, @function
main:
	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx
	movl	$0, %eax
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu 4.3.3-5ubuntu4) 4.3.3"
	.section	.note.GNU-stack,"",@progbits[/PHP]

This assembly code isn't all that bad really. There are a few underlying tricks that speed up execution. We can split this code up into 3 sections.

1.
[PHP]	leal	4(%esp), %ecx
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	movl	%esp, %ebp
	pushl	%ecx[/PHP]
For reasons unknown, modern day x86 processors seem to run quicker when their stack frame is aligned to 16 bits. Notice the bitwise AND instruction. This aligns the stack frame.

2.
[PHP]	movl	$0, %eax[/PHP]
Here is where the real program lyes. EAX is a 32-bit register. EAX also happens to work as the return dump. Whenever a function returns a value, you can bet your buck that eax, ax or al is holding the return value.
EAX - 32-bit
AX  - 16-bit
AL  - 8-bit

3.
[PHP]	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret[/PHP]
This is the inverse of section 1. Notice that there are only two pop instructions. This is because the ret instruction is a pop in disguise.

I hope that clears up a bit of confusion. If your brain is still in disarray, I'd advise you to go learn how the stack works. Wiki does an acceptable job at explaining it.

---

### Post by Thesuperchang on 2009-07-15
Although moderately irrelevant, this is how I emulated the PUSH and POP instructions for Intel's i8080 processor.

[PHP]void PUSH(void) {
	memory[SP] = C;
	SP--;
	memory[SP] = B;
	SP--;
	return;
}

void POP(void) {
	SP++;
	B = memory[SP];
	SP++;
	C = memory[SP];
	return;
}[/PHP]

In this case SP is a 16-bit register and B and C are 8-bit register which can be combined to form BC; a 16-bit register. C is the most significant byte. This processor is Big Endian. Also note that the return does nothing, I just like all my functions having a return.

---

### Post by aesis05401 on 2009-07-15
> **sidious1741 said:**
> *snip* ...Is there's a better way to learn about computer architecture (Specifically what C++ programmers should know.  I don't care about how a processor works.)

I don't want to discourage the very helpful replies that are coming from our more enlightened programming brethren, but go back to my first post in this thread.

I am no elite hacker, but I am getting into my greybeard years and I have heard young programmers ask the Assembly question a million times. 

My experience is that these programmers end up studying algorithms to get to where they want to be.  Studying algorithms will give you the vocabulary to discuss your programming technique without actually talking about a language - and this opens up a whole new world of understanding.  

Once you have this vocabulary you can literally pick up any language, learn the syntax, and begin forming well thought out code.

Best of luck.

---

### Post by sidious1741 on 2009-07-16
> **aesis05401 said:**
> I don't want to discourage the very helpful replies that are coming from our more enlightened programming brethren, but go back to my first post in this thread.

I am no elite hacker, but I am getting into my greybeard years and I have heard young programmers ask the Assembly question a million times. 

My experience is that these programmers end up studying algorithms to get to where they want to be.  Studying algorithms will give you the vocabulary to discuss your programming technique without actually talking about a language - and this opens up a whole new world of understanding.  

Once you have this vocabulary you can literally pick up any language, learn the syntax, and begin forming well thought out code.

Best of luck.

Well I don't think that I'm interested in assembly.  I really just want to know basic architecture.  I've decided to do some reading instead.

---

### Post by lisati on 2009-07-16
It's a bit of a read, but if you're interested in computer architecture, Wikipedia has an article here: [http://en.wikipedia.org/wiki/Computer_architecture](http://en.wikipedia.org/wiki/Computer_architecture)

If you're more interested in the way Linux is put together, you might find this one helpful: [http://en.wikipedia.org/wiki/Linux_architecture](http://en.wikipedia.org/wiki/Linux_architecture)

---

### Post by Thesuperchang on 2009-07-17
> **sidious1741 said:**
> Well I don't think that I'm interested in assembly.  I really just want to know basic architecture.  I've decided to do some reading instead.

If that's the case, me thinks you should go code yourself an emulator.
[http://emutalk.net/forumdisplay.php?f=30](http://emutalk.net/forumdisplay.php?f=30)
This link leads to a forum that is full of information on how to emulate old systems. Probably start off with a chip-8 interpreter then move onto a M68K or I8080.

---

