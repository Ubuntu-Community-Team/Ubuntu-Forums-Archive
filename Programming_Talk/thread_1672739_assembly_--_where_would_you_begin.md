---
title: "assembly -- where would you begin"
date: 2011-01-21
forum: Programming Talk
---

### Post by audit on 2011-01-21
I want to learn enough assembly to be able to ask intelligent questions about assembly. As a hobby programmer I have found that I can be more productive at my day job since I have learned to write a little C++ over the last year.

Now I find that there are certain problems that I really don't understand because I have no understanding of real low level programming.

So I want to learn to write in assembly and to do some basic exercises. 

Where would you begin?

---

### Post by i.n.g.o. on 2011-01-21
Hm.

i would start reading this:
[http://en.wikipedia.org/wiki/Assembly_language](http://en.wikipedia.org/wiki/Assembly_language)

a quick search on the net also brought up this:
[http://www.freebyte.com/programming/assembler/](http://www.freebyte.com/programming/assembler/)

and this:
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

i.n.g.o.

---

### Post by audit on 2011-01-21
The reason I want to learn assembly is because I do not really understand the errors messages my complier sends me sometimes. I do not understand segment faults, stack overflow and memory addresses are Greek to me.

I just want to learn enough to ask questions and find answers.

---

### Post by Simian Man on 2011-01-21
I learned by just taking some C programs (NOT C++ ones), compiling them with the -S flag and poking through the generated assembly.  Figure out what is going on, try to make changes to the program at the asm level.  Look stuff up that doesn't make sense etc.  Then again I already knew MIPS and Sparc assembly pretty well from school, so it was easier to pick up x86.

It's good to know how assembly works, but not really worth it to master that skill imho.

---

### Post by ratcheer on 2011-01-21
I agree that you are better prepared if you know assembler. I used to program IBM 370 and 390 mainframes in assembler, mainly because I hated COBOL. I learned a ton about how the computers actually worked. Especially one time after a production VSAM catalog maintence program used all its memory in the middle of the night and I had to learn how to add memory by doing GETMAIN's and FREEMAIN's.

Ah, the 80's....

Tim

---

### Post by audit on 2011-01-21
How would I decide what assembler to use? Are there any good books? Are web tutorials good enough? Does the operating system I use make a difference? Does the computer I use make a difference?

---

### Post by unknownPoster on 2011-01-21
> **audit said:**
>  Does the operating system I use make a difference? Does the computer I use make a difference?

Assembly is processor specific. If your computer is x86 based, you'll be writing x86 assembly. If your computer is SPARC based, you'll be writing SPARC assembly. If your processor is z80 based, you'll be writing z80 assembly.

That being said, x86 is probably the dominant processor family in personal computers, so chances are you can natively run x86 assembly.

In my personal life, I didn't truly grasp Assembly until I received formal classroom instruction, but your experience may vary.

---

### Post by Simian Man on 2011-01-21
> **audit said:**
> How would I decide what assembler to use?
The GNU assembler is as good as any and is probably already installed.

> **audit said:**
> Does the operating system I use make a difference?
Yes.

> **audit said:**
> Does the computer I use make a difference?
Not unless you use something unusual like an PowerPC Mac or a Sparc machine.

---

### Post by audit on 2011-01-21
I have an assembler already installed "as". I took I quick look at the man page. Any suggestions on books? or on-line tutorials? Or something to beware of before I start googling. All advice is appreciated.

---

### Post by matt_symes on 2011-01-21
Hi

Assuming you want to write for the x86 architecture then you will need the Intel manuals at some point.

[http://www.intel.com/products/processor/manuals/](http://www.intel.com/products/processor/manuals/)

This is a search results by someone asking exactly the same question as you

[http://stackoverflow.com/questions/836946/basic-yet-thorough-assembly-tutorial-linux](http://stackoverflow.com/questions/836946/basic-yet-thorough-assembly-tutorial-linux)

You really won't regret learning a bit of assembler. 

Kind regards

---

### Post by audit on 2011-01-21
does it make a difference that my cpu is:"AMD Athlon(tm) II X2 240 Processor"? 

I am really not sure what X86 means I noticed that under capabilities it list x86-64.

```
*-cpu
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: 15.6.2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq

```

---

### Post by matt_symes on 2011-01-21
Hi

> does it make a difference that my cpu is:"AMD Athlon(tm) II X2 240 Processor"? 

No. It's still the X86 instruction set (with a couple of minor instruction changes).

> I am really not sure what X86 means I noticed that under capabilities it list x86-64.

Have a read of this.

[http://en.wikipedia.org/wiki/X86](http://en.wikipedia.org/wiki/X86)

> x86-64 is a 64 bit processor based on the X86 architecture and instruction set.

Kind regards

---

### Post by NathanB on 2011-01-21
Start by reading some decent books/tutorials.

This one uses Nasm in combination with the C standard library:
[http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

Install Nasm from here:  [http://www.nasm.us/](http://www.nasm.us/)

For an easy introduction from a High-Level perspective, check out 'Art of Assembly' in combination with High-Level Assembler:
[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/index.html)
[very cross-platform: Mac OSX, FreeBSD, Linux, and Windows]

On Linux, you probably already have G(as) {GNU's "as" assembler} installed (do a 'apt-get install build-essential' if you don't), in which case, this is a great introduction:
[http://programminggroundup.blogspot.com/2007/01/programming-from-ground-up.html](http://programminggroundup.blogspot.com/2007/01/programming-from-ground-up.html)

Since you have a 64-bit CPU, this one tells you how to deal with that issue:
[http://www.duntemann.com/assembly.html](http://www.duntemann.com/assembly.html)

---

### Post by AThornton on 2011-01-21
Learning assembler is an excellent way to learn How Computers Work from a software POV.   It's also (just about) the only way to really learn why high level languages do what they do and the trade-offs of doing it using X rather then Y.  

A neat thing is: once you've grasped one assembly you've pretty much grasped them all except for microprocessor (or Bit Slice!) specific dongles.  (Tho' why anyone would learn micro-coding in 2011 escapes me.)  

"How to Do It" depends on your tolerance for frustration.   :D

Working with current machines requires a  level of knowledge you may not have.  Yes, they are more powerful and, yes, they will get you to the current State-of-the-Art with fewer purchases.  Using current machines also pose a higher barrier, in terms of necessary knowledge, e.g., you've really GOT to know what a linker is and how it works in a "deep" way.  This is the High Frustration Path.  It's also a path to some REALLY nasty problems when you ... putting it bluntly ... screw up.   (As you will.  EVERYBODY does!)    Inadvertently overwriting disk storage isn't the disaster it can be if the operating system is in ROM rather than disk-resident.  

(Trust me on this one.  I've done it.  \\:D/   Crapped a VAX 11/780 by an "oopsie" in an indirect pointer.) 

A slightly more expensive (but much, much, safer) way is to find yourself a system using a Z80, 6502, 6809 or other, obsolete, processor.  One advantage is you'll learn the basic steps and concepts of assembler without having a bunch of "cruft" in the way.  A second is these older machines were designed when hobbyists used assembler on a regular basis and, thus, there is a ton of supporting documentation, examples, and tools (using the word loosely) for writing assembler.  Plus you should get, with the machine, a ton of books, documentation, & etc. on the specifics of the machine - such as the exact address of where keyboard input is shoved - as well as documents, etc., on the microprocessor the machine is built around.  You should get all of those pluses with one purchase price.  

An IBM PC would learn you the of the How's & Why's of Segmentation Faults from a hardware POV as well as software procedure(s) for detecting them, getting around them, managing them, & etc.  

Granted learning specifics of an obsolete microprocessor seems a bit of a waste of time.   But learning to "think" assembler is, I submit, the most important thing and that will carry across.

---

### Post by matt_symes on 2011-01-21
Hi

> But learning to "think" assembler is, I submit, the most important thing and that will carry across.

Very nicely put. I cut my teeth on 6502 on the BBC Micro. It never did me any harm :D

Kind regards

---

### Post by audit on 2011-01-21
> It's also a path to some REALLY nasty problems when you ... putting it bluntly ... screw up. (As you will. EVERYBODY does!) Inadvertently overwriting disk storage isn't the disaster it can be if the operating system is in ROM rather than disk-resident.

Ok--this comment scared me. I've lost operating systems before--I can handle that, but is it possible I could make my computer unusable?

---

### Post by worksofcraft on 2011-01-21
> **audit said:**
> Ok--this comment scared me. I've lost operating systems before--I can handle that, but is it possible I could make my computer unusable?

IMO you are quite safe running programs on Linux without super user privileges.

You are completely right in what you plan to do and surely universities would have recognized the merits of teaching how computers actually work with a bit of assembler :confused:

What I would say is that it would be much better to start with a RISC processor instruction set or with one that is ["orthogonal"]("http://en.wikipedia.org/wiki/Orthogonal_instruction_set") so that every addressing mode is consistently available to every instruction. Do have a google for an emulator of something simpler than the convoluted x86 with it's mind-boggling segmented memory architecture.

---

### Post by AThornton on 2011-01-21
You're not going to harm the hardware, if that's the worry.

Any decent manual coming with your assembler should give the various  "safe" and "Don't Touch!" areas specific to your computer.  The operating system manual should, somewhere, give you the same information for the OS.  I'm a newbie to Ubuntu so I can't point you to it.

Do remember, tho', with assembler you're in charge.  If you tell the machine to write at disk sector 175, it WILL write at sector 175.  The effect(s) - if any - depends on what is - or is supposed to be - at sector 175.    Same thing with memory, plopping data at address #FD6237A may, or may not, affect the OS  or another working program's function.  

At worst, you'll hose the OS and have to re-install.  

Which is what I did with the 11/780.  Essentially, I took the file names-to-physical sector information and turned a bunch of different programs, device drivers, & etc on the hard disk into one All Inclusive file so system calls to the programs, devices drivers, & etc. got ... confused.  (Shall I say.)   The system went down and I had to re-install the stuff.

Annoying but recoverable.

---

### Post by NathanB on 2011-01-21
> **worksofcraft said:**
> IMO you are quite safe running programs on Linux without super user privileges.
That is correct.  Don't run as 'root' while playing with system calls (this goes for C hackers too).  I made the mistake once and screwed-up the file-system.
> You are completely right in what you plan to do and surely universities would have recognized the merits of teaching how computers actually work with a bit of assembler :confused:
They do.
> What I would say is that it would be much better to start with a RISC processor instruction set or with one that is "orthogonal" so that every addressing mode is consistently available to every instruction. Do have a google for an emulator of something simpler than the convoluted x86 with it's mind-boggling segmented memory architecture.

"segmented memory architecture" has been obsolete for at least two decades (although there are some who still use DOS).  All modern Operating Systems (excluding FreeDOS and related projects) use virtual memory and operate the CPU in protected mode.

[http://en.wikipedia.org/wiki/Protected_mode](http://en.wikipedia.org/wiki/Protected_mode)
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)
[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

After you read those, worksofcraft, you will no longer be living in 1992.  :)

---

### Post by NathanB on 2011-01-21
> **AThornton said:**
> 
Do remember, tho', with assembler you're in charge.  If you tell the machine to write at disk sector 175, it WILL write at sector 175.  The effect(s) - if any - depends on what is - or is supposed to be - at sector 175.    Same thing with memory, plopping data at address #FD6237A may, or may not, affect the OS  or another working program's function.  


Modern OS'en will not allow you to do so.  Protected Mode means that the OS will complain if a user program attempts to access something it shouldn't.

---

### Post by audit on 2011-01-21
I have destroyed an operating system before--that is how I wound up using ubuntu.
But there was still something there or I would not have been able install another operating system. 
There has to be some software that allows be to load an operating system right? 
Is it impossible to write over that?

edit:

This is off topic please ignore.

---

### Post by AThornton on 2011-01-21
Ack.

Modern MMU should prevent non-BIOS and OS writes to protected addresses when running User Profile(s).  Relying on the hardware people to do their job is ok,there's nothing wrong with it.  It's that I prefer to _know_ where and what I need to keep my grubby little fingers out of.   If I _know_ where to keep clear and I _know_ that I'm running under User, not system, level privileges ... it makes life simplier.

---

### Post by worksofcraft on 2011-01-21
> **NathanB said:**
> 
After you read those, worksofcraft, you will no longer be living in 1992.  :)

With or without the segmented architecture, the instruction set of the x86 is still an abomination and I have every intention of leaving the assembly code I did back in 1992 for ever and ever :)

However one plan that I have in the back of my mind is to create an emulator for Knuth's MIX processor.
This would be specifically for educational purposes, so if there are any eductionalists out there... do share your views on the merits of still learning such fundamental principles... or if it can all be done much better in Python today :D

---

### Post by NathanB on 2011-01-21
> **audit said:**
> I have destroyed an operating system before--that is how I wound up using ubuntu.
But there was still something there or I would not have been able install another operating system. 
There has to be some software that allows be to load an operating system right? 
Yes.  That is called the Basic Input/Output System.
[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

Used to be, it was contained in ROM.  But on modern machines, it usually resides in some sort of Flash-RAM.

> Is it impossible to write over that?


Well, at one time the answer was no.  But, on a modern machine, it is possible.  But not by accident.  One would have to really know certain particulars about the motherboard specs in order to do it.

---

### Post by NathanB on 2011-01-21
> **worksofcraft said:**
> 
However one plan that I have in the back of my mind is to create an emulator for Knuth's MIX processor.
I once wrote an assembler for 6502.  I had planned to also write an emulator/debugger system to complete the package, but I never did get around to doing that.
> This would be specifically for educational purposes, so if there are any eductionalists out there... do share your views on the merits of still learning such fundamental principles... or if it can all be done much better in Python today :D
Well, if you are anything like me and don't care about being "cycle exact" with the timing of the emulator, then Python is perfect for the task.

---

### Post by worksofcraft on 2011-01-21
> **NathanB said:**
> I once wrote an assembler for 6502.  I had planned to also write an emulator/debugger system to complete the package, but I never did get around to doing that.

Well, if you are anything like me and don't care about being "cycle exact" with the timing of the emulator, then Python is perfect for the task.

Hum well the 6502 was a bit b4 my time but I gather it had a reasonably logical and orthogonal instruction set.

What I meant though was not if Python would be good for writing an emulator but whether it was more suitable than assembler for teaching fundamental concepts like how things are allocated in memory, how pointers work etcetera...

---

### Post by NathanB on 2011-01-21
> **worksofcraft said:**
> Hum well the 6502 was a bit b4 my time but I gather it had a reasonably logical and orthogonal instruction set.
Yes, it was some time ago.  The set is intuitive but memory-oriented.  Not much different from the 8051/52 micro-controllers that were popular until the ARM recently usurped the stage.  Come to think of it, I now remember that the 6502 was usually clocked at only 1MHz, so it would not be hard at all to approach cycle-exact.  I might just talk myself into finishing that project.  :)
> What I meant though was not if Python would be good for writing an emulator but whether it was more suitable than assembler for teaching fundamental concepts like how things are allocated in memory, how pointers work etcetera...

When did Python get pointers??   :)

Well, I suppose that one could describe it like so...
[php]
>>> a = ['the', 'cow', 'jumped', 'over']
>>> x = 2
>>> a[x]
'jumped'
[/php]
Here, 'x' is an index into a list, but, in a way, it is also a "pointer" to the third element (or seventh character) of that list.

Does that work?  Or would that just confuse people??

---

### Post by worksofcraft on 2011-01-21
> **NathanB said:**
> Yes, it was some time ago.  The set is intuitive but memory-oriented.  Not much different from the 8051/52 micro-controllers that were popular until the ARM recently usurped the stage.  Come to think of it, I now remember that the 6502 was usually clocked at only 1MHz, so it would not be hard at all to approach cycle-exact.  I might just talk myself into finishing that project.  :)


When did Python get pointers??   :)

Well, I suppose that one could describe it like so...
[php]
>>> a = ['the', 'cow', 'jumped', 'over']
>>> x = 2
>>> a[x]
'jumped'
[/php]
Here, 'x' is an index into a list, but, in a way, it is also a "pointer" to the third element (or seventh character) of that list.

Does that work?  Or would that just confuse people??

I think it would seriously confuse students.
From the many beginner questions I've seen here on this forum I would say an assembler based programming course is very much lacking.
Simple concepts like: what is a memory fetch cycle, how the stack works with function calls and local data items, static memory allocation... how are pass by value and pass by reference actually implemented, instructions v.s. data... what is a register... how does the ALU work, interrupt servicing and also controling input/output hardware.. realitive and absolute addressing modes... and many more

Would you believe recently there was a thread from someone who was soon to be doing a course on micro-controllers... which they were going to be programming in BASIC :shock:

Can you actually think of ANYTHING one could learn about micro controllers when programming in BASIC ? TBH I really really can't even begin to imagine! :popcorn:

---

### Post by hakermania on 2011-01-22
> **audit said:**
> I do not understand segment faults, stack overflow and memory addresses are Greek to me.
&#904;&#955;&#945; &#961;&#949; &#966;&#953;&#955;&#945;&#961;&#940;&#954;&#953;, &#956;&#951;&#957; &#956;&#953;&#955;&#940;&#962; &#915;&#953;&#945; &#949;&#955;&#955;&#951;&#957;&#953;&#954;&#940; &#964;&#974;&#961;&#945;... &#924;&#943;&#955;&#945; &#947;&#953;&#945; &#954;&#953;&#957;&#941;&#950;&#953;&#954;&#945; &#954;&#945;&#955;&#973;&#964;&#949;&#961;&#945;... &#932;&#941;&#955;&#959;&#963;&#960;&#945;&#957;&#964;&#969;&#957;, &#964;&#959; &#954;&#945;&#964;&#945;&#960;&#943;&#957;&#969;....

Anyway, I think you should try to Debug your program. See the segmentation fault and search for null pointers etc :)

---

### Post by CptPicard on 2011-01-22
> **worksofcraft said:**
> 
This would be specifically for educational purposes, so if there are any eductionalists out there... do share your views on the merits of still learning such fundamental principles... or if it can all be done much better in Python today :D

Well, what constitutes "fundamental principles" has been a bone of contention here for years, it's probably the most discussed issue if you recall... the high/low level languages "megathread" in particular has a lot of stuff about this.

While I certainly believe that a well-rounded programmer will have to have an understanding of those things eventually, from an educational perspective, I would dispute whether those things really are "fundamental". If one wants to understand, say, the idea of an indirect reference -- which a pointer essentially is -- array indexing does just as well. Pass-by-reference is a general conceptual issue; the high-level language approach of symbol bindings to values teaches the "idea" much more effectively than an exposition of how a compiler might implement it in something like C++.

So yes, it (learning) can be done better in Python today -- but it is not as contrary to "learning fundamental principles" as you put it. Of course coding things like microcontrollers is a special problem domain which requires knowledge specific to it.

---

### Post by matt_symes on 2011-01-22
Hi

> Well, what constitutes "fundamental principles" has been a bone of contention here for years, it's probably the most discussed issue if you recall... the high/low level languages "megathread" in particular has a lot of stuff about this.

Oh dear. Please, not that old discussion again. My programming language is bigger than yours. :sad:

I would suggest the OP already knows at least one other language and wants to understand how that language is an abstraction from the instruction set used to control the PC ?

I would suggest that is a different exercise than learning fundamental programming concepts or fundamental principles using assembler.

I would not recommend teaching assembly as a first language but rather as an augmentation of other languages to highlight (for one example) constraints placed on a language by its grammar and syntax. (i.e What actually is a cast in C and C++).

But also, IMHO, knowing a bit of assembler really does broaden the understanding of any developer, highlighting the interaction of hardware and software, although most developers do not need or want to know it.

And that is where i think from where the discussion of the high/low level languages originates. Do you need to know low level languages for most things ? No. Do they give a broader understanding ? Yes.

Right. I will run for cover ;) Understand, i have enjoyed programming in all the languages i have used both high and low level. They all have their place.

Kind regards

---

### Post by audit on 2011-01-22
... no good reason for this post so I removed it.

---

### Post by audit on 2011-01-22
thanks to all the links and the suggestions were helpful.

---

### Post by CptPicard on 2011-01-22
> **matt_symes said:**
> 
Oh dear. Please, not that old discussion again. My programming language is bigger than yours. :sad:

Nope, it's not about that. It was a fair question on a recurring subject so I provided a response. I find this to be a really interesting topic, and don't really understand why it should be seen as an instance of just that. There's more to this really...

> 
I would suggest the OP already knows at least one other language and wants to understand how that language is an abstraction from the instruction set used to control the PC ?

It was a response to worksofcraft, not the OP. :)

Compiler theory and authoring of interpreters is an interesting subject (in which an understanding of Lisp is remarkably helpful), but really, other programming languages are not "abstractions from" assembly. All Turing-complete language are equivalent, just different in how they formulate things. Of course we need a physical machine to actually run things in the real world so there needs to be some mapping between the two...

> 
I would suggest that is a different exercise than learning fundamental programming concepts or fundamental principles using assembler.


Again, it was worksofcraft's question, not the OP's. :)

> 
I would not recommend teaching assembly as a first language but rather as an augmentation of other languages to highlight (for one example) constraints placed on a language by its grammar and syntax. (i.e What actually is a cast in C and C++).

How about using Lisp as an example to highlight Assembly's limitations in not having higher-order functions, while Lisp still has the full ability to manipulate state in small steps, if desired? :)

> 
But also, IMHO, knowing a bit of assembler really does broaden the understanding of any developer, highlighting the interaction of hardware and software, although most developers do not need or want to know it.

I'm not sure I've ever made statements as to "not learning assembler"; just that I am very sceptical of the claims of its "fundamentality" in comparison to higher-level languages.

> 
And that is where i think from where the discussion of the high/low level languages originates. Do you need to know low level languages for most things ? No. Do they give a broader understanding ? Yes.

It is not a matter of "not needing to know"; it leaves me with the nagging feeling that in that case HLLs are seen as some sort of a cop-out and crutch (a bit like the term "abstraction" is used as an almost derogatory term in the LLL-circles). I'm not sure how to communicate it that the model of computation that assembly represents is *perfectly possible* in all higher-level languages as well; it's just that there is so much more to HLLs that actually aid in conceptualizing "computable things", and it is that kind of thinking that a programmer needs most.

---

### Post by NathanB on 2011-01-22
> **worksofcraft said:**
> I think it would seriously confuse students.
From the many beginner questions I've seen here on this forum I would say an assembler based programming course is very much lacking.
Simple concepts like: what is a memory fetch cycle, how the stack works with function calls and local data items, static memory allocation... how are pass by value and pass by reference actually implemented, instructions v.s. data... what is a register... how does the ALU work, interrupt servicing and also controling input/output hardware.. realitive and absolute addressing modes... and many more
Well, those are 'beginners' -- one cannot expect them to already know about things they've not yet been exposed to.  Just like any other bailiwick, it takes time and experience to develop new skills.  Also, in order to obtain most of the more advanced programming skills, one has to be a bit of an autodidact.  Most people do not posses the ability to teach themselves... and they don't know where to look to find these answers even if they had the desire to know.

Someone once posted this Competency Matrix:
[http://www.starling-software.com/employment/programmer-competency-matrix.html](http://www.starling-software.com/employment/programmer-competency-matrix.html)

Heck!  I do not have any desire, nor intent, to be at 'Level 3' on every one of those categories.  Do you??  Does anyone??

> Would you believe recently there was a thread from someone who was soon to be doing a course on micro-controllers... which they were going to be programming in BASIC :shock:

Can you actually think of ANYTHING one could learn about micro controllers when programming in BASIC ? TBH I really really can't even begin to imagine! :popcorn:

Perhaps the goal of the course was **not** to teach about micro controllers?  Embedded environments require attention to much more important issues...  and, yes, C, Basic, Java, etc. are perfect languages for teaching these concepts.

---

### Post by worksofcraft on 2011-01-22
> **NathanB said:**
> 
Perhaps the goal of the course was **not** to teach about micro controllers?  Embedded environments require attention to much more important issues...  and, yes, C, Basic, Java, etc. are perfect languages for teaching these concepts.

Hum... well I did do quite a lot of work on embedded controllers. and IMO several of those languages are far from "perfect". The problems you have to face can include:
[LIST]
[*]No operating system available
[*]extremely restricted memory
[*]program must run from read only memory
[*]need to consider concurrency
[*]need to handle hardware interrupts
[*]need to access volatile hardware register values
[*]need to consider latency
[*]need to recover gracefully from bugs/malfunction
[*]not crash when there is performance overload
[*]absence of floating point hardware
[*]absence of dynamic memory management
[*]absence of standard library
[*]Need to write all your own I/O routines for OEM hardware.
[*]primitive and buggy cross compilers
[/LIST]

IMO there is no point having a course about embedded controllers that simply looks at how to code correct algorithms. You can do that much better on your desktop.

The issue of 'beginners' is relevant to this thread, as it is about the didactic value of exposure to assembly level language.

Frequently I see threads about confusion between pointers and arrays, pass by reference and return by value. Recently there was one that showed they simply had no concept of an immediate value as opposed to a so called constant l-value.

Personally I feel these things can be explained very clearly in assembler while I also appreciate that Cpt. Picard feels they are best explained at a more abstract level.

I would compare it to explaining how the internal combustion engine works either in terms of pistons, valves and spark plugs or in terms of exothermic chemical reactions, Boltzman constants and adiabatic thermodynamic processes.

... it kind of suggests this might be a subjective question of personal preferences :shock:

---

### Post by NathanB on 2011-01-23
> **CptPicard said:**
> Compiler theory and authoring of interpreters is an interesting subject (in which an understanding of Lisp is remarkably helpful), but really, other programming languages are not "abstractions from" assembly. All Turing-complete language are equivalent, just different in how they formulate things. Of course we need a physical machine to actually run things in the real world so there needs to be some mapping between the two...

[QUOTE=matt_symes]I would not recommend teaching assembly as a first language but rather as an augmentation of other languages to highlight (for one example) constraints placed on a language by its grammar and syntax. (i.e What actually is a cast in C and C++). 
[/QUOTE]
[QUOTE=CptPicard]
How about using Lisp as an example to highlight Assembly's limitations in not having higher-order functions, while Lisp still has the full ability to manipulate state in small steps, if desired? :)
[/QUOTE]

One could port Simple Machine Language to Lisp.  Perhaps even present it in a cushy interface similar to _why's_ Hackety-Hack?

[http://freshmeat.net/projects/sml](http://freshmeat.net/projects/sml)

---

### Post by CptPicard on 2011-01-23
> **NathanB said:**
> One could port Simple Machine Language to Lisp.  Perhaps even present it in a cushy interface similar to _why's_ Hackety-Hack?


Sure. Implementation wouldn't be difficult either; just underlying registers and a list of modification-statements that are run against those registers.

An interesting added bonus could be that the student could modify the instruction implementations or something and see what for example the SBCL compiler outputs for the code :p It's often surprisingly readable, and when optimizing Common Lisp, it's often interesting to see what kind of stuff some particular part gets compiled to.

---

### Post by matt_symes on 2011-01-23
Hi

Well this is not a discussion i am going to get into as it will go around and around ( potentially creating another mega thread ;) ). 

If the OP wants to learn assembler the i, for one, will not try to dissuade him.

Kind regards

---

