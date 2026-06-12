---
title: "Tools for programming - Beginner needing guidance."
date: 2008-05-13
forum: Programming Talk
---

### Post by rlameiro on 2008-05-13
Well, Hello to everyone!!!

I apologize in advance for my English. I hope it is readable.

I have Ubuntu 8.04 installed with the metapackets for ubuntustudio -audio.
Laptop dell d600 centrino 1.4.

After the introducing here goes my beginner questions.

Since I am starting to learn the C language i would like to know what the best graphic tools to code. IDE, debuggers etc. also any nice tutorials to start programming in C are welcomed, I have already find some ([www.mindview.net](www.mindview.net)) and other. My tiny background in programing comes with some knowledge of basic (not visual, but the spectrum and calculators one :) ), and in assembly for microcontrollers PIC and 8085. 

The objective of learning C is that for start leraning languages from the base. first c then c++, then java, then maybe PHP/ruby/pearl etc.

Also asking if it is advised to learn pascal based languages like delphi etc? if I have the c founded only it is ok?

after thinking in using some "graphic software making" like QT/GTK/WxWidgets and alike.

thanks in advance

---

### Post by LaRoza on 2008-05-13
> **rlameiro said:**
> 
Since I am starting to learn the C language i would like to know what the best graphic tools to code. IDE, debuggers etc. also any nice tutorials to start programming in C are welcomed, I have already find some ([www.mindview.net](www.mindview.net)) and other. My tiny background in programing comes with some knowledge of basic (not visual, but the spectrum and calculators one :) ), and in assembly for microcontrollers PIC and 8085. 

The objective of learning C is that for start leraning languages from the base. first c then c++, then java, then maybe PHP/ruby/pearl etc.

Also asking if it is advised to learn pascal based languages like delphi etc? if I have the c founded only it is ok?

after thinking in using some "graphic software making" like QT/GTK/WxWidgets and alike.


For C, see the sticky. It has a walkthrough for compiling and running a program using C and the most common Linux tool. For tutorials, see my wiki.

Pascal and its friends are dead for the most part. Although there are implementations alive, they are not worth learning unless you really want to.

The sticky and my wiki have references for GUI programming.

---

### Post by dwhitney67 on 2008-05-13
For debugging C (or C++) code, you can use 'gdb', and if you prefer a graphical front-end to it, then 'ddd'.

When compiling C/C++ code, specify the -g option so that symbolic information of the code can be used.  For example:

```
$ gcc -g MyFile.c -o MyApp
$ ddd MyApp &
```

---

### Post by CptPicard on 2008-05-13
> **rlameiro said:**
> 
The objective of learning C is that for start leraning languages from the base. first c then c++, then java, then maybe PHP/ruby/pearl etc.

That is not necessarily the right way to do things though. You're really not gaining anything from that order of things. You do learn C and C++ (and then get stuck learning C++ for the next 5 years), then you don't really transfer much into Java, you don't want PHP in general and Ruby/Perl are better replaced with Python, which you should have started to begin with.

You're under the typical beginner misconception that there *is* this kind of a ground-up order of languages to begin with... there really isn't. The only stuff you'll transfer from C are basic programming constructs, which you can more easily learn starting with a higher-level language to begin with. And once you've got those down, tackling the specifics of C in due time is much more comfortable.

---

### Post by pmasiar on 2008-05-13
In other words, beginner is much better off when start learn programming in Python. We had lots of discussion about it here, even a poll - see sticky FAQ.

Python will let you focus on programming basics, taking care of all typecasting and declarations - works much harder for you than  C. Also, it;s data structures are easier and more flexible to define, use - less lines of code, less dark corners for bugs to hide from you.

See wiki in my sig to get started.

---

### Post by dwhitney67 on 2008-05-13
Yep, Python is great for those who want instant gratification when programming.  But as to understanding how the "nuts and bolts" work, well that will never happen when using Python... perhaps it is best not to know.

---

### Post by solarwind on 2008-05-13
It is pretty much unanimous here that Python is the best language to learn as a beginner. However, I say start with C, then move to C++ or Java.

> **dwhitney67 said:**
> Yep, Python is great for those who want instant gratification when programming.  But as to understanding how the "nuts and bolts" work, well that will never happen when using Python... perhaps it is best not to know.

I think that it's best to learn how the computer works from the start (shared objects, libraries, linking, code origin, 16/32 bits in 8086 assembler, and so on). I *started* on that stuff and I'm still alive. ;)

@ Your comment about the PIC assembler, what PIC chip(s) do you have? I work with PICs a lot and I could help you out if you needed.

---

### Post by pmasiar on 2008-05-13
> **solarwind said:**
> However, I say start with C, then move to C++ or Java.


... or, if you are into this kind of fun, start with Forth, then continue with brainfuck :-)

---

### Post by solarwind on 2008-05-13
> **pmasiar said:**
> ... or, if you are into this kind of fun, start with Forth, then continue with brainfuck :-)

LOL, that's nothing, try the [LOLCODE]("http://lolcode.com/") language.

---

### Post by CptPicard on 2008-05-13
If you really want the "nuts and bolts" experience (which of course you should get at some point in life), sure, learn C (after Python). But there simply is no reason to go through Java or C++ after that... there is nothing that really enlightens you enough in those languages. Just go straight to Lisp :-)

One should remember that even assembly isn't really the low level these days anymore. Modern CPUs just emulate the instruction set... the microcode is something completely different!

---

### Post by solarwind on 2008-05-13
> **CptPicard said:**
> If you really want the "nuts and bolts" experience (which of course you should get at some point in life), sure, learn C (after Python). But there simply is no reason to go through Java or C++ after that... there is nothing that really enlightens you enough in those languages. Just go straight to Lisp :-)

One should remember that even assembly isn't really the low level these days anymore. Modern CPUs just emulate the instruction set... the microcode is something completely different!

Java and C++ give you a true object oriented experience complete with modifiers, packages and so on. They teach you a LOT about proper structure and code formation.

Also, please elaborate on your words here:

> One should remember that even assembly isn't really the low level these days anymore. Modern CPUs just emulate the instruction set... the microcode is something completely different!

---

### Post by NateMan on 2008-05-13
I think he might be referring to how modern microprocessors are less hardware recently and more software that seems to be hardware placed on the chip.

---

### Post by Lux Perpetua on 2008-05-14
There's an additional layer of translation between machine code instructions and what the processor actually implements directly, but this translation is implemented entirely in the hardware. I've never bothered myself with this; it's an implementation detail of the processor that has no bearing on functionality. However, I imagine that it would become more important if you wanted to understand why some instructions are faster than others.

---

### Post by CptPicard on 2008-05-14
> **solarwind said:**
> Java and C++ give you a true object oriented experience complete with modifiers, packages and so on. They teach you a LOT about proper structure and code formation.

Which is, essentially, the kind of "proper structure and code formation" that you need to work around the straightjacket that a statically typed OOP language puts you in. You may not want to go there in the first place. And mind you, this coming from primarily a Java guy of most of the past decade. :)

I am personally very disillusioned about OOP design patterns and such... they seem like such a bunch of contortions. I really got my enjoyment in programming back when I moved to a more flexible OO system such as Python's, which let you actually describe your problem instead of solving "architectural problems" which need not even be there in the first place.

Currently I am hacking with CLOS, and let me tell you, that is an object system done right. It solves absolutely trivially a lot of the nasty "how do I put program entities together to achieve this" problems I have come across during my career so far :) 


> **Lux Perpetua said:**
> I've never bothered myself with this; it's an implementation detail of the processor that has no bearing on functionality.

Exactly, and assembly itself is *"an implementation detail that has no bearing on functionality"*. From the program's perspective, it doesn't know, nor does it care, what sort of machine it is running on, as long as the semantics of the language are satisfied. For example for Java code, it might just as well be running on a JVM CPU -- it doesn't know. Lisp code might well be running on a Symbolics Lisp machine that does Lisp in hardware, or SBCL... same thing.

And yes, Lux is right about what I'm trying to get at -- a long time ago in a galaxy far away, x86 assembly actually was x86 assembly in the hardware. There really was a correspondence with the actual metal to the instructions you were running. Time has moved on however, and the instruction set is kept for compatibility, but what actually happens in the hardware happens more and more in terms of the CPU's micro-ops... under the hood the whole thing is much more complex than an old 386, but it just looks like one from the outside. :)

---

### Post by rlameiro on 2008-05-14
> **solarwind said:**
> 
@ Your comment about the PIC assembler, what PIC chip(s) do you have? I work with PICs a lot and I could help you out if you needed.

Well I am not an expert in PICs ... I'm just a curius trying to make some stuff with them :) The pics I have are various as I made som sampling in microchips website. all within the 16F - 18F range, but also interested in working with the powerful ones 24F, and the 32 bits ones.

Maybe I wasn't explicit enough in my first post. I need to learn C. C++ and JAVA are optional. Why? C is a system language is the most close High language to the machine... It is hard, well it seems so, but there is not much support for other languages like python for PICmicro. However I would also like to learn PC programming languages to interface with the little projects, and I already found that there is a good amount of libraries for hardware interfacing (USB, RS232, etc..). I found an assembly translator for the python language, so I will invest some time learning Python as almost everyone advised.

About assembly in x86 processors, well they aren't really x86 processors anymore, prove of that are the constant new specification launched by the processor makers... 3dnow, SSEs, etc. but still the internal architecture is quite the same, just with a little twist. 

So programming in assembly, even with an hardware translation layer, will be always faster than with other programming languages (well unless you mess with it a lot) also in critical timing programming, you don't have much choice for programming 'chips'. And as I am a musician who wants to work with audio analysis and tempo/time division well interrupts control and timing routines ... not a chance Assembly :( 

Anyway, thank you all and please continue to post your ideas and comments, you are really 'opensource' minded people!!! finally!!!!!:guitar:

---

### Post by pmasiar on 2008-05-14
> **solarwind said:**
> Java and C++ give you a true object oriented experience complete with modifiers, packages and so on. They teach you a LOT about proper structure and code formation.


LOL **true object experience** - are you in sales dept? :-)

And teaching proper code structure? In Python, code structure **has syntactic meaning**. And don't get me started about the Java is, OO? Which important OO feature Java has which Python lacks? 

Java is not Object-oriented - it is [object-obsessed](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) and you seems like a [blub programmer](http://www.paulgraham.com/avg.html) with little if any experience with dynamically typed languages - you should get some, your life will change forever.

---

### Post by dwhitney67 on 2008-05-14
Seems that this thread has degenerated into another "which programming language is best" discussion.  :-({|=

The OP probably has decided to give up on programming altogether and decided to focus on a business major.

---

### Post by pmasiar on 2008-05-14
maybe it was you "nuts and bolts" gentle nudge to move it in direction to flamewars? :-)

Because then we can ask, which level is "nuts and bolts" enough: C++? C? Why not ASM? And in fact, microcode simulates the CPU architecture for us, even if you do not want to change it.

My claim is "nuts and bolts" is level where user can comfortably and independently solve problems s/he has. Computers are here to help us as much as we let them to, CPU is idling for work, any work. There is no need for a programmer mind to be wasted on static typing, unless there are **business** reasons why it is necessary. No learners need that at the first pass, IMHO.

---

### Post by Sinkingships7 on 2008-05-14
> **dwhitney67 said:**
> Seems that this thread has degenerated into another "which programming language is best" discussion.  :-({|=

As most threads around here tend to do. And they always will.

The OP did not ask "Hey, what language should I use? Which one's the best?". So let's stop answering the question that never came up in the first place, please? It does get pretty aggravating. Now, there's no doubt that Python is a fine language, but that's a different point entirely. He did not ask about Python, nor did he ask why it's the superior, god-sent language everyone makes it out to be.

He wants to learn C. I think that's a great idea. I think that even if i *didn't* think it was a great idea, it's not my place to tell him how he should go about his programming career. 

To the OP: the forums over at [www.cprogramming.com](www.cprogramming.com) might be of use to you.

---

### Post by CptPicard on 2008-05-14
The OP certainly has a very good reason for learning C -- it has its place -- but it doesn't mean that all arguments that may came around in these kinds of threads are equally acceptable. In particular the point about Java or C++ being good learning languages because of OOP "enforcement" is dubious to the max, and it deserves to be questioned, regardless of OP's merits :)

---

### Post by rlameiro on 2008-05-15
Well! I think everyone has a point in what concerns programming. which is the best way to go in the beginning etc... However for a beginner I think that there are different ways to go. Maybe it will depend on the objective that he/she wants to learn in the firs place. 

In my case I want to learn C because it is easier and faster to program microcontrollers, and also to make some programming for pc, but python in my case (I am taking some tutorials and online lectures) its becoming quite nice to learn and to start doing something that works fast. 
Maybe you are right to say that c++ and Java is not so good for a beginner programmer, and really it wasn't a priority learn C++ and Java. I just wanted to know some programming language that works and is easy to do in the beginning.
also just wanted to do it in a cross platform language, else I would go to visual basic express and everything will be already solved :)

Anyway thank you all for your help

Last question... dumb i think...
it is possible to make a stand alone binary program with python Tkinter for windows? also for linux? something tha do not needs to make something like this $python program.py ??? It will need to be compiled but I will like to know that, because if its not possible i don't need python anyway...

---

### Post by vexorian on 2008-05-15
Learn C/C++ and one of those toy languages *simultaneously*. C++ can teach you C's pointers crazyness and some of its strange OOP model at the same time, then you can also try python.

Those who think learning C will not help you with the toy languages, I think you are making a big mistake. The toy languages are very easy to use, but therefore they are also very easy to use wrong... Some consciousness about how strings have to work when actually implemented in a lower level will help you code more efficient code in the higher level languages.

Oh, and indentation is not good code structure, it is just indentation and nothing else, I can code you a terribly structured program in python that's just as unreadable and unmaintainable as your typical C code if I want to.

--
Anyways, if you want to just do some code, you can skip to the toy language, if you want to learn programming, learning one of the C's and many other languages is the best idea, after python try lisp or haskell, you'll be surprised. Also try coding in whitespace one day (not actually in whitespace, but try to make code using that logic)

Do not forget the theory, a good book on algorithms is something you should want to read if you really are interested in learning programming.

---

### Post by pmasiar on 2008-05-15
"Toy languages"? Get off your high horse!

Python is good enough for NASA and Google, might be good enough for you. Kiddies tinker with C and recompile kernel for fun, professionals are using the best tool for the job: creating best value with least effort.

---

### Post by CptPicard on 2008-05-15
I'm not sure if that was a troll or not but let's go anyway.. ;)

> **vexorian said:**
> C++ can teach you C's pointers crazyness ....
The toy languages are very easy to use, but therefore they are also very easy to use wrong...

IMO it's the "pointer crazyness" that makes C easy to use wrong. And combined with C++'s constructors/destructors you really need to start going deep into "how to write proper C++" before you even actually manage to get anything done.

These "toy languages" actually often let you express things in different ways, and most of those ways aren't necessarily "wrong" (although there may be elegance/aesthetical considerations..)

> Some consciousness about how strings have to work when actually implemented in a lower level will help you code more efficient code in the higher level languages.

Uh... it's just a sequence type. The efficiency considerations work on a higher level there, we're not interested how they are "implemented" (and that's the point -- the implementation should be efficient under the hood already).

> Anyways, if you want to just do some code, you can skip to the toy language

You can do a *lot* of fascinating code in a toy language. Actually, you can do code you would be hard pressed to achieve in C (barring essentially writing the runtime system for the other language).

> if you want to learn programming, learning one of the C's and many other languages is the best idea

You learn nothing else except the basic control structures from C (because there *is* nothing else), and you can learn them from any other language. I honestly do not understand what it is that makes people feel C is educational :)

Is it the pointers? Just use an array and index into that, it's the same thing... (I wish had thought of this counter-argument in that one pointers discussion with Shining Arcanine...)

> after python try lisp or haskell, you'll be surprised.

Got to agree with Lisp, it's great. Haskell is a bit nasty in the sense that you have to go through monad-like contortions to get stateful computations...

> 
Do not forget the theory, a good book on algorithms is something you should want to read if you really are interested in learning programming.

Exactly... the most important thing to remember is that the language is just a tool, the actual issues are abstract.

---

### Post by solarwind on 2008-05-15
> **pmasiar said:**
> "Toy languages"? Get off your high horse!

Python is good enough for NASA and Google, might be good enough for you. Kiddies tinker with C and recompile kernel for fun, professionals are using the best tool for the job: creating best value with least effort.

You seem to be one of those arrogant know-it-all script kiddies. Now I don't mean offense, but your posts are very single sided and arrogant. NASA uses Python, true that. But not Python only. Guess what language Python is written in, smart-***? You got it, big shot! C.

Vexorian is not saying anything negative. I agree with him fully. All he's saying is that C is good to learn simultaneously. However, your posts seem to be very egocentric and one sided - Python. Python is a great language, I love it, but C and C++ still teach many fundamental concepts to anyone wanting to learn. You can't program a PIC microcontroller in Python (don't give me a wise *** response telling me to use a translator). You need to use C or an assembler directly.

Don't take me the wrong way, this isn't a personal attack, but I'm just showing you the mirror, you may want to chose your words carefully before sounding like a goodie-two-shoes.

---

### Post by Wybiral on 2008-05-15
> **solarwind said:**
> You seem to be one of those arrogant know-it-all script kiddies. Now I don't mean offense, but your posts are very single sided and arrogant. NASA uses Python, true that. But not Python only. Guess what language Python is written in, smart-***? You got it, big shot! C.

Not necessarily, ever heard of PyPy?

Do you think the first C compiler was written in C?

I don't want to get into the chick-and-egg debate with you, but because a language was written in another doesn't mean anything. I can write a C compiler in Python. What's your point?

---

### Post by Wybiral on 2008-05-15
> **solarwind said:**
> You can't program a PIC microcontroller in Python (don't give me a wise *** response telling me to use a translator). You need to use C or an assembler directly.

ok.

---

### Post by CptPicard on 2008-05-15
> **solarwind said:**
> You seem to be one of those arrogant know-it-all script kiddies. Now I don't mean offense, but your posts are very single sided and arrogant.

IMO he just shows that when you've got enough experience in the field, you start appreciating efficient tools :)

> NASA uses Python, true that. But not Python only. Guess what language Python is written in, smart-***? You got it, big shot! C.

And guess what language the processor understands? You got it, assembler... and not only that, there is microcode there too!

From the program's perspective, it is irrelevant what you're running on. It may be the bare hardware, it may be some kind of virtual machine. Totally, absolutely irrelevant. Most importantly, C does not bring anything to the table that from the algorithmic perspective it would be strictly stronger. Neither are any other languages of course, but having stuff like lambdas can go a long way.

> You can't program a PIC microcontroller in Python (don't give me a wise *** response telling me to use a translator). You need to use C or an assembler directly.

And I can't write Java bytecode from C :( Specialized applications need specialized tools.

---

### Post by pmasiar on 2008-05-15
> **solarwind said:**
> You seem to be one of those arrogant know-it-all script kiddies. Now I don't mean offense, but your posts are very single sided and arrogant.

LOL, I write opinionated answers to arrogant posts, like 'toy language' above. Get used to that. :-)

> Guess what language Python is written in, smart-***? You got it, big shot! C.

How it is relevant? We were talking about needs of beginners. Writing compilers is not what beginners do - unless they are as smart as you, of course :-)

> Vexorian is not saying anything negative. I agree with him fully. All he's saying is that C is good to learn simultaneously.

Worst ever advice for a beginner, struggling to understand syntax of one language: learn two different syntaxes at once. maybe you want to share the stuff you are smoking, sounds strong?

> However, your posts seem to be very egocentric

maybe python-centric? :-)


> but C and C++ still teach many fundamental concepts to anyone wanting to learn. 

Show me one of my posts where I advised against learning C. But always as a **second language** not the first! 

> You can't program a PIC microcontroller in Python (don't give me a wise *** response telling me to use a translator). You need to use C or an assembler directly.

L33t hackers can do it Forth. I know I did :-) and it is more fun that way :-)

---

### Post by LaRoza on 2008-05-15
> **solarwind said:**
> You seem to be one of those arrogant know-it-all script kiddies. Now I don't mean offense, but your posts are very single sided and arrogant. NASA uses Python, true that. But not Python only. Guess what language Python is written in, smart-***? You got it, big shot! C.


I see this is getting personal...

Thread Closed for review.

(Yes, I took part in this thread, but I do not think I need to have another mod deal with this)

---

