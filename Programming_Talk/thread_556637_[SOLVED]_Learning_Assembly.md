---
title: "[SOLVED] Learning Assembly?"
date: 2007-09-21
forum: Programming Talk
---

### Post by happysmileman on 2007-09-21
I'd like to learn x86 assembly for Linux, but have no idea how to start.

I need an assembler, linker and text editor.  And books

Basically I want to be able to use assembly (not Higher level assembly, no macros or anything) just to learn about how the computer (and Linux) works internally, I don't really want GUI, though extra points if I can later set it up to use QT.

So what do people recommend for:

1: Assembler/Linker
2: Text editer/IDE (I use KDE and prefer not to have GTK/GNOME apps)
3: Books/resources, preferably with focus on Linux (I can and will try order one, but not old enough for credit card, so if you have good online one post that as well, but would prefer real book)

---

### Post by Wybiral on 2007-09-21
1. Nasm or GAS. Either one, or learn both, you'll realize they are the same thing with minor picky details. I suggest NASM first, then GAS, but it's up to you.

2. Text editor... Any. Doesn't matter.

3. Assembly is really simple. Just grab the developers manual for your processor and some introductory tutorials online. There are only a handful of mnemonics for most processors, I don't think you need a complete book to pick it up.

Then I suggest you start studying the output of compilers, GCC for instance because it will teach you how to think C code into assembly and structure your assembly. Then you can write C and have a good idea what the assembly will look like... Then you can stop using assembly, lol.

---

### Post by happysmileman on 2007-09-21
> **Wybiral said:**
> 1. Nasm or GAS. Either one, or learn both, you'll realize they are the same thing with minor picky details. I suggest NASM first, then GAS, but it's up to you.


Will do.

> 
2. Text editor... Any. Doesn't matter.


Done :P

> 
3. Assembly is really simple. Just grab the developers manual for your processor and some introductory tutorials online. There are only a handful of mnemonics for most processors, I don't think you need a complete book to pick it up.

I googled and found several conflicting things about Pentium 4 manual, so I have a few questions.
Any idea where I could get that manual? (the obvious one)
Is it free?
Download or book?
Would it be easy to get (as in would a bookshop order it for me?)

---

### Post by samjh on 2007-09-21
> **happysmileman said:**
> I googled and found several conflicting things about Pentium 4 manual, so I have a few questions.
Any idea where I could get that manual? (the obvious one)
Is it free?
Download or book?
Would it be easy to get (as in would a bookshop order it for me?)

They're free from the horse's mouth:

[http://www.intel.com/products/processor/manuals/index.htm](http://www.intel.com/products/processor/manuals/index.htm)

For the Pentium 4, you'll be looking at IA-32 (aka. x86-32bit) documentation.

You should probably have a look through this too:
[http://en.wikibooks.org/wiki/X86_Assembly](http://en.wikibooks.org/wiki/X86_Assembly)

---

### Post by Wybiral on 2007-09-22
> **samjh said:**
> ... You should probably have a look through this too:
[http://en.wikibooks.org/wiki/X86_Assembly](http://en.wikibooks.org/wiki/X86_Assembly)

Wow, that's a really good source of info on assembly!

---

### Post by LaRoza on 2007-09-22
My wiki in the library, look in my sig. Lots of Assembly info there.

---

### Post by happysmileman on 2007-09-22
Thanks, looked through all the links, got the intel PDF's, an e-book and bookmarked some stuff... thanks for that

---

### Post by emperon on 2007-09-23
what about fasm ?

---

### Post by samjh on 2007-09-23
> **emperon said:**
> what about fasm ?
[http://en.wikipedia.org/wiki/FASM](http://en.wikipedia.org/wiki/FASM)

The two most popular assemblers for Linux is GAS and NASM, so it's best to use those, instead of more obscure (and perhaps more limited) ones like FASM.

On Windows, the de facto standard is MASM.

---

### Post by Mr_Smiley on 2007-09-23
Hi,

I found the book "Programming from the Ground Up" to be quite useful in learning assembly.

You can download it from here:
[http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

---

### Post by happysmileman on 2007-09-23
Ok I know this is marked as solved, and I thought it was.

Every tutorial I bookmarked is just a page or two long and assume you already know DOS assembly.
The Intel docs are thousands of pages in total, and appear to be way more detailed than anyone needs (good as a reference once you know a lot of ASM).

Anyone have a tutorial (for NASM) that:
Explains the common instructions (what you need to do most basic stuff, so far I only really know ADD,SUB, INT and MOV because none of the tutorials even name any others),
Preferably is Linux-oriented (though i have the system calls list so not necessary),
Is up to date ,
Doesn't assume you already know ASM (I already know C++ and some C so doesn't need to be a "for dummies" book though)

---

### Post by LaRoza on 2007-09-23
> **happysmileman said:**
> 
Anyone have a tutorial (for NASM) that:
Explains the common instructions (what you need to do most basic stuff, so far I only really know ADD,SUB, INT and MOV because none of the tutorials even name any others),
Preferably is Linux-oriented (though i have the system calls list so not necessary),
Is up to date ,
Doesn't assume you already know ASM (I already know C++ and some C so doesn't need to be a "for dummies" book though)

My wiki, has exactly that tutorial in the Assembly section. NASM for Linux for Beginners. 

Unfortunately, most Assembly tutorials assume you know something or have some experierence.

You will probably need to use many sources for a more complete course.

[http://docs.cs.up.ac.za/programming/asm/derick_tut/#references](http://docs.cs.up.ac.za/programming/asm/derick_tut/#references)

[http://asm.sourceforge.net//intro/Assembly-Intro.html](http://asm.sourceforge.net//intro/Assembly-Intro.html)

[http://asm.sourceforge.net/](http://asm.sourceforge.net/) (Not a tutorial, but good to browse)

(are you using Opera)

---

### Post by Wybiral on 2007-09-23
> **happysmileman said:**
> Ok I know this is marked as solved, and I thought it was.

Every tutorial I bookmarked is just a page or two long and assume you already know DOS assembly.
The Intel docs are thousands of pages in total, and appear to be way more detailed than anyone needs (good as a reference once you know a lot of ASM).

Anyone have a tutorial (for NASM) that:
Explains the common instructions (what you need to do most basic stuff, so far I only really know ADD,SUB, INT and MOV because none of the tutorials even name any others),
Preferably is Linux-oriented (though i have the system calls list so not necessary),
Is up to date ,
Doesn't assume you already know ASM (I already know C++ and some C so doesn't need to be a "for dummies" book though)

There's some Linux specific INTRO to assembly documents I wrote a while back here: [http://p13.wikispaces.com/asm](http://p13.wikispaces.com/asm)

I never finished it (I may got back to edit and finish it, depends on the demand), and the edges are a little rough, but it should make sense to anyone who already knows a bit about computer science and wants to learn some assembly.

---

### Post by LaRoza on 2007-09-23
> **Wybiral said:**
> There's some Linux specific INTRO to assembly documents I wrote a while back here: [http://p13.wikispaces.com/asm](http://p13.wikispaces.com/asm)


Very nice! Wish I found them earlier. Adding them to my wiki :D.

---

### Post by happysmileman on 2007-09-23
> **LaRoza said:**
> My wiki, has exactly that tutorial in the Assembly section. NASM for Linux for Beginners. 


I'm sorry, but I don't see a tutorial by that name or that fits the description in the Assembly section, followed all the links.

> (are you using Opera)

Yes

---

### Post by tgbrowning on 2007-09-23
If you can find a copy of Spontaneous Assembly, you'd be miles ahead of the game. It's old, from before 1995 and Windows but is the most incredible bit of coding I've ever seen. The documentation is astonishing and can show you ways to do really modular programming using only Assembly Language.  You're best bet is to try eBay or possibly abebooks.com and search them.  

I just wish I still had my copy.  

The material was origianlly written for ASM and C programmers and employs all of the capacbilities you can discover using make and makefiles. Conditional compilation is a snap and extremely easy to tailor to your own needs.  

Browning>>>

---

### Post by LaRoza on 2007-09-23
> **happysmileman said:**
> I'm sorry, but I don't see a tutorial by that name or that fits the description in the Assembly section, followed all the links.


At the moment, the Library doesn't really describe the links, I will change that soon.

They are in the post above. The first one is the "Learn Assembly" link, and the other is described as a "Tutorial (NASM)".

Sorry, for indescriptive links. I will work on changing them to titles of the article or tutorial.

I wish I could use the new versions of Opera like you (9.23), I am using 9.10 because I am using the portable version.

---

### Post by happysmileman on 2007-09-23
> **LaRoza said:**
> They are in the post above. The first one is the "Learn Assembly" link, and the other is described as a "Tutorial (NASM)".


Ag, got it, though it's still not very detailed, but did teach me some stuff, especially about system calls.

> There's some Linux specific INTRO to assembly documents I wrote a while back here: [http://p13.wikispaces.com/asm](http://p13.wikispaces.com/asm)

Thanks, looks perfect,, shame about it not being finished, and as far as I can tell, there's ALWAYS a demand for good ASM tutorials, no-one I know seems to have EVER gotten a good ASM tutorial, they all assume you already know ASM, especially the ones for Linux, and the ones for Windows are so out-dated it doesn't matter anyway, the code pretty much never works without a lot of modifying

---

### Post by Wybiral on 2007-09-23
> **happysmileman said:**
> Thanks, looks perfect,, shame about it not being finished, and as far as I can tell, there's ALWAYS a demand for good ASM tutorials, no-one I know seems to have EVER gotten a good ASM tutorial, they all assume you already know ASM, especially the ones for Linux, and the ones for Windows are so out-dated it doesn't matter anyway, the code pretty much never works without a lot of modifying

With as rapidly as the environment changes, it's no surprise they're outdated (even the up-to-date ones today will be outdated in a year or so).

I think it's great to know assembly for educational reasons, but it's not a practical language to develop in these days at all... No portability what-so-ever, scales terribly, long development cycles, and even with good code and commenting it's a nightmare to manage... It's a dying language.

I think this is why it's hard to find good info on assembly. Plus, for anyone who does know DOS assembly, going to Linux is just a matter of learning some new system calls (and a new assembler, but assembly is assembly no matter what it looks like).

But, once you get the basics down, you will be able to figure everything out yourself using the intel developers manual and a good understanding of computer science.

---

### Post by happysmileman on 2007-09-23
> **Wybiral said:**
> With as rapidly as the environment changes, it's no surprise they're outdated (even the up-to-date ones today will be outdated in a year or so).

Well I've compiled examples for Windows 95 on a Windows XP computer with very little change, so the basics stay relatively similar, there are new opcodes with each new generation of processor, and of course system calls change. But the basic remain the same for a long time.

> I think it's great to know assembly for educational reasons, but it's not a practical language to develop in these days at all... No portability what-so-ever, scales terribly, long development cycles, and even with good code and commenting it's a nightmare to manage... It's a dying language.

It's dying for actually developing programs, but it will ALWAYS have its uses, for example boot-loaders, parts of OS kernels and of course optimising algorythms and complex graphics etc, and of course debugging...
It'll always be used and always be considered a valuable skill to have. And the less people learn it the more valuable it gets, though it's a shame people don't seem to realise this.

---

### Post by Mr_Smiley on 2007-09-24
Hi,

Did you take a look at the book that I have mentioned above? This books describes assembly without any assumption of previous knowledge and assumes that you are programming under GNU/Linux. I have found it to be a very useful book. Take a look, it might be what you are looking for:

[http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

The only thing is that the book describes using gas (GNU as) rather than nasm, but I believe that it teaches the basics of assembly well.

Hope this helps,
Thanks. :)

---

### Post by hockey97 on 2007-09-24
Hi, I would like to know what's the pro's of using assembly??

I want to make a small eletronic device using my bread board, I am trying to make a small computer on the board, and plan to build the cricuit myself and also make the OS for the system.
I was thinking to use assembly or Might use c++.

I am doing such a project just to get experience,
I done small projects at my highschool/college class.

so I just want to learn and have fun while doing my own thing.
in other words I want to have a reward after I work on somthing, in this case, I am trying to make a desktop type pc,but with no case , just to mess around and get my hand into stuff...

any suggestions????
I don't want to spend more than 1,000 bucks or so on this.

---

### Post by Wybiral on 2007-09-24
> **hockey97 said:**
> Hi, I would like to know what's the pro's of using assembly??

I want to make a small eletronic device using my bread board, I am trying to make a small computer on the board, and plan to build the cricuit myself and also make the OS for the system.
I was thinking to use assembly or Might use c++.

I am doing such a project just to get experience,
I done small projects at my highschool/college class.

so I just want to learn and have fun while doing my own thing.
in other words I want to have a reward after I work on somthing, in this case, I am trying to make a desktop type pc,but with no case , just to mess around and get my hand into stuff...

any suggestions????
I don't want to spend more than 1,000 bucks or so on this.

I've never made an eletronic cricuit or somthing, lol, jk (but seriously, you should really use a browser with built-in spell checking like Firefox).

My advice... Write an OS for an existing machine first so you will have a better understanding when trying to... Design a processor???

It's you again!

My first question is this... Where are you going to get a C++ compiler for your home-rolled processor? You're not. So if you have any hope at all (and there isn't any considering the physical limitation of using a breadboard for a processor) but for the sake of conversation... You'll need a SOLID understanding of assembly.

Why? Well... What the heck do you think a processor does? Magic? lol. Nope, it processes machine code which is a byte representation of assembly (actually, assembly is a textual representation of machine code, but you get the point).

To put it bluntly... You cannot design your own computer and write the OS for it if you don't understand what assembly is. So go out, ditch the hardware idea for now, and learn assembly. Then try to write a "Hello World" OS for an EXISTING computer (an old 20 dollar piece of crap will do).

If you can't do this, you can't build your own.

---

### Post by Carl Hamlin on 2007-09-25
> **hockey97 said:**
> I want to make a small eletronic device using my bread board, I am trying to make a small computer on the board, and plan to build the cricuit myself and also make the OS for the system.


Kudos to you - I love applied science. Lemme know if you've got specific questions while you're going about it - I may or may not have been there before.

> **hockey97 said:**
> I don't want to spend more than 1,000 bucks or so on this.

Here, you're probably out of luck. If your experience is anything like mine, you're going to try to work with cheap materials for a bit and get frustrated with your results, then try it out with more expensive stuff and get frustrated with your results, but for different reasons.

*grin*

 This is an expensive hobby, and will alienate your spouse faster than anything else I know of.

---

### Post by samjh on 2007-09-25
> **Wybiral said:**
> My first question is this... Where are you going to get a C++ compiler for your home-rolled processor? You're not. So if you have any hope at all (and there isn't any considering the physical limitation of using a breadboard for a processor) but for the sake of conversation... You'll need a SOLID understanding of assembly.

Why? Well... What the heck do you think a processor does? Magic? lol. Nope, it processes machine code which is a byte representation of assembly (actually, assembly is a textual representation of machine code, but you get the point).

For a home-rolled processor, he'll need to know machine code. :D

Perhaps it will be better to go punch-cards instead. :p

---

