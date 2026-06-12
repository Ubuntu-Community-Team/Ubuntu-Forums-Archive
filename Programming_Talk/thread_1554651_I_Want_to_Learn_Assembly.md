---
title: "I Want to Learn Assembly"
date: 2010-08-17
forum: Programming Talk
---

### Post by Jaiichi on 2010-08-17
I'm heading off to my first year of university soon, studying Computer Engineering. I've been interested in teaching myself some assembly language, but I'm not totally sure how to go about this, so it'd be nice to get some guidance to start me out.

I'm moderately familiar with programming at this point, I've been working with Pascal for about 3 years (ugh, don't ask) and over the last year I've learned Java (Mostly self-taught). I've heard a lot that a moderate level of understanding C is preferred? I assume my Pascal knowledge can help me a little with that, plus I believe C is the language they teach first-years at my university.

I've tried to look around to get some vague understanding of what is required to start things going towards learning more about architecture and data handling and such (or something, I'm still fairly confused).

So whats an easy way to go about teaching myself it? I figure I'd like to purchase a book if I could find an applicable one.

One thing I've at least caught on to is that it's very hardware specific. I'd probably be wanting to do this on my computer with an Intel Atom N450 Processor and Ubuntu as the OS.

So, if my questions make sense (I really hope I'm not totally off the ball), what do I need to do?

---

### Post by worksofcraft on 2010-08-17
I learnt to program in assembly language and I totally support the view that you will get a far superior understanding of computer programming than all the high level languages put together could ever teach you.

It starts to get interesting when you know the exact difference between call by value and call by reference and consequences of allocating variables on the heap, or the stack and how polymorphism ands virtual methods translate into machine code.

However, sadly modern desktop processors are simply too complicated: You need to get a more primitive processor to start with. Alas I can't give you any pointers at the moment, but will be interested to see what others recommend.

Best of luck and I'll be watching your thread :)

---

### Post by Jaiichi on 2010-08-17
My processor isn't primitive enough? I thought a processor that uses the x86 instruction set can do Assembly. (I really don't completely know what I said, but I have a fairly good feeling what I said might be correct). And from what I feel the Atom N450 can use it.

If I'm completely wrong is there anything that could, uh, "emulate" a more primitive processor? I have a feeling what I said is fairly... stupid?

What are the requirements to be able to code some assembly, if both my upper points are completely off the mark?

---

### Post by GenBattle on 2010-08-17
I think it depends what level of knowledge you're already at. You seem to have a reasonable amount of knowledge already with the range of languages you know.

I don't know about your course, but first year in my course involved teaching people in the class the very basic fundamentals of programming. In our case we were using Delphi, doing basic algorithmic development (mathematical expressions, data structures, control structures, etc.). Generally i found that in uni computer science/engineering courses, 60-70% of people came in with no (or very little) prior programming experience.

I would suggest at this point that you wait until you get to uni. Good lecturers can be the most knowledgeable people you will meet anywhere (and sometimes the least knowledgeable). Most lecturers will be happy to see you shooting ahead of the class, and will be more than happy to help you progress your knowledge further.

If you're working on an Atom processor then your instruction set is x86, here's some useful links i googled for you:
[http://en.wikipedia.org/wiki/X86_assembly_language](http://en.wikipedia.org/wiki/X86_assembly_language)
[http://en.wikibooks.org/wiki/X86_Assembly](http://en.wikibooks.org/wiki/X86_Assembly)
Looking at the wikibooks material, i would think it would be enough to get you started at the very least.

Personally i found the most rewarding experience in terms of learning how assembler and computer architecture works was building a simple compiler. At uni our lecturer had made a simple VM in C, with an accompanying simple Assembler language of its own (although we didn't have to compile the assembler into binary). Our task was then to use the instruction set available (which was fairly simple) to make a compiler for a simple programming language, but this was more to learn how a compiler was built than how to learn assembly.

Generally speaking, the only place assembler is used is high-performance applications, embedded programming, or compiler construction.

---

### Post by GenBattle on 2010-08-17
> **Jaiichi said:**
> My processor isn't primitive enough? I thought a processor that uses the x86 instruction set can do Assembly. (I really don't completely know what I said, but I have a fairly good feeling what I said might be correct). And from what I feel the Atom N450 can use it.

If I'm completely wrong is there anything that could, uh, "emulate" a more primitive processor? I have a feeling what I said is fairly... stupid?

What are the requirements to be able to code some assembly, if both my upper points are completely off the mark?

I think he means to start with an instruction set smaller than pure x86 (x86 is huge, and most of it you won't use) and a VM (just as i did when learning to build a compiler). My suggestion would actually be to get a microcontroller like an 8051 (or an 8051 emulator) and use that for learning.

---

### Post by schauerlich on 2010-08-17
> **worksofcraft said:**
> I learnt to program in assembly language and I totally support the view that you will get a far superior understanding of computer programming than all the high level languages put together could ever teach you.

It will give you a superior understanding of a specific implementation of a stack-based register machine, sure. But programming in general? In my mind, at least, computer programming is much more abstract than that. You certainly gain a good insight on how to optimize lower level code or to debug odd stack corruption errors, but I would say that's less learning about computer programming and more about how to deal with the rough edges of an imperfect model of computation.

> However, sadly modern desktop processors are simply too complicated: You need to get a more primitive processor to start with. Alas I can't give you any pointers at the moment, but will be interested to see what others recommend.

Best of luck and I'll be watching your thread :)

You can get 90% of the benefit of learning assembly (what you mentioned above) by only learning 10% of the instruction set. I'd recommend learning from a book that aims to teach you about the PC architecture over one that tries to teach you the whole of the Intel instruction set. Try [this book](http://heather.cs.ucdavis.edu/~matloff/50/PLN/CompSystsBookS2010.pdf) (PDF warning) by one of my professors. I found it pretty easy to follow if you pay attention.

---

### Post by worksofcraft on 2010-08-17
Yeah like Genbattle said, certainly x86 can do assembly but the instruction set is phenomenally complicated with different modes and memory pages and well then it has to run under Linux and know how to interact with X windows. Just writing a "Hello, world!" program in assembler would involve so many concepts it would put you off for life :(

look I'll give you an example:
```

	.file	"hello-1.c"
	.section	.rodata
.LC0:
	.string	"Hello, world!\n"
	.text
.globl main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	.cfi_personality 0x3,__gxx_personality_v0
	pushq	%rbp
	.cfi_def_cfa_offset 16
	movq	%rsp, %rbp
	.cfi_offset 6, -16
	.cfi_def_cfa_register 6
	movl	$.LC0, %edi
	movl	$0, %eax
	call	printf
	leave
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 4.4.3-4ubuntu5) 4.4.3"
	.section	.note.GNU-stack,"",@progbits

```

The C code for that is:
```

#include <stdio.h>
int main(void) {
	return printf("Hello, world!\n");
}

```

and if you want to experiment, then let me suggest the -S command line switch for g++ compiler ;)

p.s. the statements that start in a . are 'directives' that tell the assembler to do something.
The ones that are indented by a tab bit don't start in . are actual instructions that your processor will execute.
labels like main: simply give a name to a particular memory address so that you don't have to specify it's numerical value...

Uhmm... yeah I'll go check that book that schauerlich mentions... sounds interesting... oh and nice thread btw  :)

---

### Post by Lootbox on 2010-08-17
I don't know much assembly, but I would definitely say that some experience in C really helps you understand low-level memory allocation much better.

---

### Post by GenBattle on 2010-08-17
> **Lootbox said:**
> I don't know much assembly, but I would definitely say that some experience in C really helps you understand low-level memory allocation much better.

Agreed. Assembly simply gives you a more detailed understanding of how/why it happens. You don't really need this detail unless you intend to work with microcontrollers or other embedded hardware.

---

### Post by mmix on 2010-08-17
learn c programming in 10 years.

[http://norvig.com/21-days.html](http://norvig.com/21-days.html)

[http://csapp.cs.cmu.edu/](http://csapp.cs.cmu.edu/)

---

### Post by DanielWaterworth on 2010-08-17
> **schauerlich said:**
> ...but I would say that's less learning about computer programming and more about how to deal with the rough edges of an imperfect model of computation...

I totally agree, people don't appreciate that programming isn't only imperative, but that it can also be declarative.

---

### Post by lordhaworth on 2010-08-17
Hi,

For a comprehensive look at assembly - try "The Art of Computer Programming" By Donald Knuth. Its basically a book of algorithms  using a hypothetical assembly code "MIX". 

It is certainly comprehensive but also guides the reader into the assembly code gently. I would recommend it, but you would be hard pressed to read the whole thing "as a book" - it is best to pick and choose what you would like to look at once you have been through the introduction to MIX

---

### Post by CptPicard on 2010-08-17
> **worksofcraft said:**
> I learnt to program in assembly language and I totally support the view that you will get a far superior understanding of computer programming than all the high level languages put together could ever teach you.


Oh, the HLL vs. LLL issue again... lots about it said here: [http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794)

So if we had a programmer who only coded in assembly, he would have a superior understanding to someone who had coded in everything else except assembly? I think not; the idea of state-changes by operations and how you solve issues in that model would have come around in other languages.

For example when it comes to things like virtual function resolution in C++, it's the semantics of the operation that matter, not the underlying implementation. Knowing how it's implemented does not add anything to your ability to actually understand how it works and how to use it.

---

### Post by nvteighen on 2010-08-17
Learning Assembly has been my biggest disappointment in several years. Forth was way more interesting... C makes even more sense nowadays.

Ok, it gives you insight on how the architecture works and that's useful for understanding several of the shortcomings C has (for example, call stack overflow.)

But it gives you no insight on anything else. Conceptually, it gives you nothing and it's supposed to be that way or it would be a high-level language, useless for what Assembly is meant to be used. Programming is about abstracting stuff (usually procedures, but not only, like in the case of declarative programming) into a formal-logical language that a computer can interpret somehow... but the computer is "nothing more than an interpreter" (C-3P0) and you can tell what the code is about if you know the language and the libraries used.

Of course, it won't hurt you, but don't expect more than what Assembly is able to offer: a mnemonic for opcodes.

---

### Post by NathanB on 2010-08-17
You will find many links to lots of useful x86 ASM resources here:  [http://www.delicious.com/Evenbit](http://www.delicious.com/Evenbit)

Hope that helps on your quest.

---

### Post by worksofcraft on 2010-08-17
> **CptPicard said:**
> Oh, the HLL vs. LLL issue again... 
... and similar.

It is my experience that quite a few aspiring programmers hardly appreciate the difference between an interpreted language and a compiled one these days.

They have no idea how the various busses in the system actually work and seem surprised when you tell them that pointers on a 64 bit architecture are 8 bytes while they are only 4 bytes on a 32bit system...

They do not understand the difference between passing paramaters and returning results by value or by reference... "why are all those copy constructors getting called and why does the pointer to that local variable I returned no longer point to something valid?"

[COLOR="Lime"]*It isn't about which language is better. It is about gaining an understanding of computers that you don't get at high levels of abstraction.*[/COLOR]

I also wish to endorse the recommendation by lordhaworth. Those books by Knuth are classics. IMO it would be great if anyone has written a MIX emulator for didactic purposes 8-[

---

### Post by GenBattle on 2010-08-17
> **CptPicard said:**
> Oh, the HLL vs. LLL issue again... lots about it said here: [http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794)

So if we had a programmer who only coded in assembly, he would have a superior understanding to someone who had coded in everything else except assembly? I think not; the idea of state-changes by operations and how you solve issues in that model would have come around in other languages.

For example when it comes to things like virtual function resolution in C++, it's the semantics of the operation that matter, not the underlying implementation. Knowing how it's implemented does not add anything to your ability to actually understand how it works and how to use it.

I think knowing how a compiler/virtual machine works is far more valuable to your knowledge of programming than learning any particular assembler language.

---

### Post by schauerlich on 2010-08-17
> **worksofcraft said:**
> ... and similar.

It is my experience that quite a few aspiring programmers hardly appreciate the difference between an interpreted language and a compiled one these days.

C can be interpreted, and python can be compiled. It's a matter of implementation which is completely divorced from the language itself. I can take the same (portably written) .c file and run it with any number of different compilers/interpreters and as long as it correctly implements the C language, I don't have to know if it's compiled, interpreted or sent to the President.

> They have no idea how the various busses in the system actually work and seem surprised when you tell them that pointers on a 64 bit architecture are 8 bytes while they are only 4 bytes on a 32bit system...

They do not understand the difference between passing paramaters and returning results by value or by reference... "why are all those copy constructors getting called and why does the pointer to that local variable I returned no longer point to something valid?"

See, but these things only *matter* at a low level of abstraction. Computation is an abstract concept that is wholly independent of what architecture it runs on. While knowing low level details is certainly important for working in C, C++ and assembly, one could be a completely competent programmer in Scheme without knowing anything about pointers or 64bit vs. 32bit.

---

### Post by worksofcraft on 2010-08-17
> **schauerlich said:**
> C can be interpreted, and python can be compiled. It's a matter of implementation which is completely divorced from the language itself. I can take the same (portably written) .c file and run it with any number of different compilers/interpreters and as long as it correctly implements the C language, I don't have to know if it's compiled, interpreted or sent to the President.


That is why I would recommend an understanding of assembler. From a purely logical point of view it may not matter if the language is interpreted or compiled, however from the point of understanding how computers work, it does.

Perhaps it doesn't matter "to the president", but a programmer ought to be aware that C and C++ are the way they are so they map effectively onto underlying computer architecture, while languages like Prolog are almost purely abstract logic.

In academic circles programming may be a purely abstract concept but to others the reality is important. Different people have different ways of understanding things and thinking about them: To me, a mental image of indexing a method though an object's class v-table is far more intelligible than some kind of abstract notion of polymorphism.

---

### Post by mmix on 2010-08-17
assembly could be fun when it comes with hardware stuff.

Build a Microcomputer, AMD, 1976-1979.  A series of seven booklets describing designs using AMD's am2900 family of bit-slice parts.   The parts of the series are:
[http://www.homebrewcpu.com/links.htm](http://www.homebrewcpu.com/links.htm)

[http://en.wikipedia.org/wiki/PDP-11_architecture](http://en.wikipedia.org/wiki/PDP-11_architecture)

[http://en.wikipedia.org/wiki/Code:_The_Hidden_Language_of_Computer_Hardware_and_Software](http://en.wikipedia.org/wiki/Code:_The_Hidden_Language_of_Computer_Hardware_and_Software)

---

### Post by eeperson on 2010-08-17
> **worksofcraft said:**
> 
I learnt to program in assembly language and I totally support the view that you will get a far superior understanding of computer programming than all the high level languages put together could ever teach you.

> **worksofcraft said:**
> 
It isn't about which language is better. It is about gaining an understanding of computers that you don't get at high levels of abstraction.


I disagree with your initial statement that assembly gives you a better understanding of *programming* than a high level language.

I agree with your second statement that assembly gives you a better understanding of *computers*.

I get the impression that you equate understanding computers with understanding programming (correct me if I'm wrong).  This seems like a false equivalence.  I would argue that understanding computers has very little to do with understanding programming concepts in general (complexity theory, abstraction, etc.).  These concepts can be learned through assembly but they are much less clear.

---

### Post by worksofcraft on 2010-08-17
> **eeperson said:**
> I disagree with your initial statement that assembly gives you a better understanding of *programming* than a high level language.

I agree with your second statement that assembly gives you a better understanding of *computers*.

I get the impression that you equate understanding computers with understanding programming (correct me if I'm wrong).  This seems like a false equivalence.  I would argue that understanding computers has very little to do with understanding programming concepts in general (complexity theory, abstraction, etc.).  These concepts can be learned through assembly but they are much less clear.

That's why I said "understanding computer programming". It involves understanding both computers **and** programming. I'll concede that my initial statement was perhaps a bit extreme, but so is the opposite (and apparently popular) conception that implications of the underlying mechanics would be irrelevant.

Anyway I just wanted to give some encouragement to the OP instead of being negative about it.

---

### Post by Jaiichi on 2010-08-17
Hey guys, thanks for all the responses, I think I will more or less take the advice of whoever said I could wait it out a bit and talk to a/some prof about it. If he believes learning it would provide a better overall understanding, then I'll probably go through with it, since it will likely compliment how he/she views computers as a whole.

During this waiting it out period, I think I'll start learning a good portion of the more basic C syntax, (hopefully around the point of the things i knew in Pascal and Java), since i'm 100% I'll be learning that come September.

---

### Post by Bachstelze on 2010-08-17
> **Jaiichi said:**
> Hey guys, thanks for all the responses, I think I will more or less take the advice of whoever said I could wait it out a bit and talk to a/some prof about it. If he believes learning it would provide a better overall understanding, then I'll probably go through with it, since it will likely compliment how he/she views computers as a whole.

I'll paraphrase CS:APP and say that the knowledge of assembly (and related concepts) is what makes the difference between a programmer and a good programmer.  When you're a programmer, you will inevitably face situations where your program will behave in a non-intuitive way (see for example [this thread]("http://ubuntuforums.org/showthread.php?t=1552313")).  Knowing how things work under the hood will give you the ability to know how and why such weird behaviours arise, and correct them.  Otherwise, you will either have to assume that your program will never reach such a state (and Murphy's law will apply), or ask someone who do (and who is probably paid higher than you).

---

### Post by Jaiichi on 2010-08-17
> **Bachstelze said:**
> I'll paraphrase CS:APP and say that the knowledge of assembly (and related concepts) is what makes the difference between a programmer and a good programmer.  When you're a programmet, you will inevitably face situations where your program will behave in a non-intuitive way (see for example [this thread]("http://ubuntuforums.org/showthread.php?t=1552313")).  Knowing how things work under the hood will give you the ability to know how and why such weird behaviours arise, and correct them.  Otherwise, you will either have to assume that your program will never reach such a state (and Murphy's law will apply), or ask someone who do (and who is probably paid higher than you).

I've always been leaning towards the idea that it'll be very beneficial for me. And I've got nothing to lose really. It isn't like learning it will make things worse for me, but I'm going to give it some time before I really go into it.

---

### Post by xb12x on 2010-08-17
Anyone wanting to learn assembly coding should have a look at PC BIOS code. It's all written in assembly. 

And since the standard PC BIOS has been around since the first PC-AT, and not re-designed since then (~ 1985), for the most part you'll see a very _small_ subset of today's huge x86-x64 instruction set.  

If you do a little Googling you can find different attempts at an open-source PC BIOS, with source files. And you'll see how a PC powers up, how all the hardware is initialized, and how the O.S is loaded and run, etc.

---

### Post by DanielWaterworth on 2010-08-18
> **Jaiichi said:**
> I think I'll start learning a good portion of the more basic C syntax

The syntax of C is only a small part of C and is relatively simple. The most important bit is to learn is the way people use it. People tend to write reusable object-orientated code which doesn't initially sound possible.

---

### Post by CptPicard on 2010-08-18
> **worksofcraft said:**
> 
[COLOR="Lime"]*It isn't about which language is better. It is about gaining an understanding of computers that you don't get at high levels of abstraction.*[/COLOR]


Yes, it's not about which language is "better". There is certainly a point regarding understanding *computer architecture*, but the computer architecture in itself is totally devoid of any higher ideas, and contrary to what some people seem to believe, it does not *inform* the programmer about those higher ideas in any way.

Whether something like a vtable actually tells you something meaningful about the idea of polymorphic types is quite debatable, IMO. The fact that you feel it's enlightening is probably a case of mental imprinting into a certain model of thinking (not saying it's bad, it's just something that exists).

---

### Post by nvteighen on 2010-08-18
> **CptPicard said:**
> Yes, it's not about which language is "better". There is certainly a point regarding understanding *computer architecture*, but the computer architecture in itself is totally devoid of any higher ideas, and contrary to what some people seem to believe, it does not *inform* the programmer about those higher ideas in any way.

Ok, I'm not sure of what my point is, but...

To understand computer architecture you don't need Assembly... Assembly might help you and to learn it you need previous computer architecture knowledge, but I could learn about x86 CPUs without ever coding a single instruction in Assembly: books, e.g.

On the other hand, you only can learn how to program by using some language... no matter of C, Assembly, Java, Common Lisp or your own homebrewed programming language. It's still a language... And you still can write any of those without a computer; if you know them well enough, you'll be able to interpret them in your mind.

---

### Post by DanielWaterworth on 2010-08-18
> **nvteighen said:**
> And you still can write any of those without a computer; if you know them well enough, you'll be able to interpret them in your mind.

Once you start executing instructions in your mind you are no longer devoid of a computer. In the 18th century being a computer was a profession.

---

### Post by CptPicard on 2010-08-18
> **DanielWaterworth said:**
> Once you start executing instructions in your mind you are no longer devoid of a computer.

But that is still just a mental model of computation, that can get pretty ingrained. If people are too used to executing instructions in their mind, that's what they will expect... I guess what I am more used to is mapping things functionally, and the imperativeness part is used when needed.

---

### Post by nvteighen on 2010-08-19
> **DanielWaterworth said:**
> Once you start executing instructions in your mind you are no longer devoid of a computer. In the 18th century being a computer was a profession.

Of course, but my point was that you can do this without a computer, ideally. Obviously, first, we get tired and a computer doesn't and that's a reason to use them :)

But what I wanted to show is that computers are just a tool, not the goal of programming... except for that subset of programming that is devoted to "set them up" for using them (e.g. low-level programming). That's possible because computers are also part of the reality we can model using a programming language.

---

