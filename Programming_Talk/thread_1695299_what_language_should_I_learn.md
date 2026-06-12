---
title: "what language should I learn ?"
date: 2011-02-25
forum: Programming Talk
---

### Post by Shadowstripe on 2011-02-25
I have experience working with ASP/SQL and wanted to get into a proper language but I am unsure where to start ? do I go with C, C++ or C# ? 

Thinking I don't want spend to much time into something if its just going to be no good further down the line (think the version of asp I was working with at the time has gone that way).

I did have a quick play with C# thinking that new will be better (this is on my windows box) and what I got through was not to hard to understand coming from asp, I did run into a few errors using my current tutorial (googling seemed to point to the latest XNA version not been backwards compatible with what the tutorial was suggesting)  That got my thinking should I be trying something different ?

any suggestions? should I (re)start with a different language ? (also like the idea of using whatever language with openGL over directX for portability) but bare in mind I'm trying to keep it simple for now.

:) Thanks

---

### Post by cgroza on 2011-02-25
I do recommend Python and C++. You may wish to start with python, depending on you level of knowledge in programming.

---

### Post by Nico-dk on 2011-02-25
I'd recommend Python too.

Picked it up last weekend, and I now consider myself an expert ... Actually not, but it is REALLY easy to pick up. I'm by no means what you'd consider a programming prodigy, but in the past 8 days, I've made a script, that'll do a system status calling several tools (like you would from the terminal) when run, and save parts of the output to a file. Also managed to make a simple game for the Ubuntu terminal, and i'm currently working on an actual application.
It's that easy, and there are a truckload of guides, tutorials, references out there on the wild wild web.

---

### Post by IWantFroyo on 2011-02-25
Try them all! The ones I would recommend trying are Java, C#, and Python. Java is my personal favorite, but I have a friend who adores C# (he thinks it's better than C++, and I have no experience with C so I'm going to trust him). Just a warning: C only runs on the computer you make it on. If you get a C application, you're going to have to compile it yourself. A version of C is worth trying a bit of just because it's so ubiquitious. 
My recommendation: give Java a try, and maybe Python. If you don't prefer any of those over C#, then just try to work your C# problems out.

---

### Post by Shadowstripe on 2011-02-25
Thanks for the input

---

### Post by foxmuldr on 2011-02-25
> **Shadowstripe said:**
> any suggestions? should I (re)start with a different language ? (also like the idea of using whatever language with openGL over directX for portability) but bare in mind I'm trying to keep it simple for now.

Are you wanting to be a developer, or a coder?  If you want to be a developer, then I would recommend learning Intel's x86 assembly (not the AT&T syntax).

Learning assembly and understanding the machine at its most primitive levels will give you a unique, fundamental understanding of why things work the way they do in a computer program.  You will see through operating systems, through applications, through any layers of interpretation, and directly to the raw "bones" of the machine.

If you get a firm handle on assembly language, and the underlying architecture and why things work they way they do, everything you ever try to do will almost be second nature to you, because that foundation will give you the philosophy of "how things should work" ... and then you can see how the author of the app did it to give you whatever it was in a way which works -- as there are many paths to "successful results."

Hope this helps.

- Rick C. Hodgin

---

### Post by ve4cib on 2011-02-26
It really depends on the kind of programming you want to be doing.  If all you're interested in is AJAX and web programming then don't waste your time with Assembly, C, C++, and other relatively low-level languages.  Instead focus your efforts on languages that are used on the web: Javascript, PHP, Python, C#, Java, Perl, Ruby, and suchlike.

If you're more interested in doing OS/Kernel/Driver development, or working with embedded systems where there may not even be an operating system in place then C or C++ is the way to go.  For embedded systems a good knowledge of the assembly language instructions for the CPU you're working with is also a very good idea.  (Common embedded CPUs I've run into are the AtMega128, Motorolla 68k, and ARM.)

If you're just starting off as a programmer and have no idea what you want to do (i.e. you want to test the waters and you'll figure out what you're interested in as you go) then I'd suggest either Java, C# (if you're using Windows -- Visual Studio is a wonderful IDE, and one of the few Microsoft programs I can honestly say I enjoy using), or Python.

Python is arguably one of the easiest languages to pick up.  The tutorials are clear and numerous, the syntax is easy, and the code is designed to be legible by a human.  I've heard it described as "executable pseudo-code."

Java gets used a lot in introductory university courses.  It offers enough flexibility that you can do some pretty low-level stuff.  Not as low as C or Assembly, granted, but still pretty low.  But unlike C it also scales up very easily to very large, complex applications.

If you're interested in learning Java from the beginning I suggest you look at this wiki: **[COMP1010 Wiki Textbook](http://wiki1010.cs.umanitoba.ca/mediawiki/index.php/COMP1010)**.  It's the online textbook used by the University of Manitoba for their introductory computer science course.  You may find it helpful.

(Note for anyone else who checks out the textbook: it doesn't cover objects, polymorphism, or any of that jazz.  That's covered in COMP1020, the second introductory course.  1010 is pretty much procedural programming in Java.  And unfortunately I don't think there's a 1010 textbook wiki (yet).)

---

### Post by nvteighen on 2011-02-26
> **foxmuldr said:**
> Are you wanting to be a developer, or a coder?  If you want to be a developer, then I would recommend learning Intel's x86 assembly (not the AT&T syntax).

Learning assembly and understanding the machine at its most primitive levels will give you a unique, fundamental understanding of why things work the way they do in a computer program.  You will see through operating systems, through applications, through any layers of interpretation, and directly to the raw "bones" of the machine.

If you get a firm handle on assembly language, and the underlying architecture and why things work they way they do, everything you ever try to do will almost be second nature to you, because that foundation will give you the philosophy of "how things should work" ... and then you can see how the author of the app did it to give you whatever it was in a way which works -- as there are many paths to "successful results."


Oh man, you're mixing so many things there...

No, ASM will give you some foundations for low-level programming and will explain some incongruencies that happen in C and C++, but it's completely irrelevant for programming in general. Well, not even that, try applying ASM to a low-level language like Forth and you're lost.

Programming is more about writing about some computable reality in a certain formal language, which usually happens to be simulated/interpreted by a computer. You know, if you know C and I hand you some code written in it, you'll surely understand it without a computer. 

Of course, because programs are coded for computers primarily, some languages incorporate computer-specific semantics for implementation reasons. That's what defines low-levelness: aspects in programming language's specs that refer to the computer, in contrast to those that refer to general processes/objects of thought.

But you don't need to learn ASM to learn Common Lisp. Not even if the particular Common Lisp implementation you use is written in ASM. Moving registers and using labels in ASM won't explain what a closure is. The mistake here is to think that programming languages form a continuum that starts in binary and presumably ends in some sort of Lisp. But that's not true: programming languages, save some exceptions (e.g. C++, Objective-C), aren't conceptually based on others, but created from new. Then you implement the interpreter of the language (not the language!) in some other programming language. For instance, there are C++ compilers for the JVM...

Are low-level languages necessary? Of course. Should they be learned? Of course. But when it comes to understanding what programming is from a general, conceptual, point of view, high-level languages are better.

P.S.: About learning Intel ASM vs. AT&T ASM *syntax*... That's irrelevant: the semantics of both are quite the same. I could understand you said it's better to learn either NASM (which is Intel syntax) or GNU AS (which is AT&T, but supports Intel) or some other ASM implementation because it has such or such feature you think it's interesting... That'd a semantics discussion, which is what you really want to discuss when evaluating what programming language you want to use.

---

### Post by cguy on 2011-02-26
I wouldn't recommend learning Python as the first language.

It may be dead simple to pick up (ie: one week MAX from zero to advanced skills), but its downside is that you will be concentrating on using Python specifics (lists, Python strings etc.) instead of concentrating on concepts that'd allow you to make a simple transition to any programming language.


I recommend C.
The language itself is tiny, really. Learn to use its libraries (input, output, memory allocation and other commonly used ones) and you'll have a solid understanding of what programming really is about.

Not to mention that you can use C anywhere: from microcontrollers to desktop applications to kernel development, on virtually any available platform.

Its downside is that it'd take more effort than with eg. Python to write something complex.


C++ (with STL) is a whole different beast. Writing C++ code is much different from writing C code (unless, of course, you choose to write "C with classes & cin & cout").
You can also choose C++, but you'd have to memorize more things.

Its major advantage is that it's OOP, a crucial aspect if you want to get employed quickly.



[B]REMEMBER: no matter which language you choose, learn it with the help of a GOOD BOOK + the occasional tutorial.
Tutorials alone are not good enough to keep you interested or to give you a direction to build something useful.[/B]

---

### Post by Some Penguin on 2011-02-26
> **Shadowstripe said:**
> I have experience working with ASP/SQL and wanted to get into a proper language but I am unsure where to start ? do I go with C, C++ or C# ?

C might be interesting if you want to force yourself to learn about particular architectures, because C doesn't bother to hide them from you.  Incompletely specified type sizes, a not terribly large set of routines in the actual language definition providing less guarantees of universality... e.g. threading.

C and C++ and the like also have one particular drawback that makes it somewhat less appealing for complex projects:  the ability to write data to arbitrary locations within a process's allocated memory makes it *much* easier to very subtly corrupt data structures and the like.  Writing to a completely invalid location like 0x0 is relatively simple to find and fix because it'll trigger an immediate fault; writing into an unrelated, existing in-memory data structure within same process's address space defining a financial transaction and not noticing until long after the now corrupt data is written to persistent storage is another matter.   This ability to read and write throughout the processes's allocated memory also makes it trickier to write completely secure code.  It may be frequently theoretically possible to manually create highly optimized C code that may take less CPU time, but I suggest that this may often be a poor use of *human* time because the difficulty of isolating bugs can make it considerably more painful to find and fix them, and it increases a system's vulnerability to the fallibility of *every* author of every library it invokes.

Haven't really looked at C#, at all, so no comments there other than I would expect that they've thought about how to lessen some of the more painful aspects of C and C++.

Personally, I find Java very practical.  It's mature enough that there's a pretty large set of APIs built into the language, and modern and widely used enough that there's a lot of highly useful third-party code (JDBC drivers, Maven, Tomcat, log4j, JUnit, IntelliJ, Yourkit, Guava, Guice, Spring...).  The ability to create small anonymous classes and generics is convenient if one wants to take a somewhat functional approach as well, since it facilitates function composition.  The reflection API makes it quite doable for code to inspect objects and invoke methods by name or the like, in the usual case (it is more obnoxious if you are simultaneously dealing with generic and varargs methods, because determining which identically named function in the same class is the most appropriate to invoke for a given set of arguments takes more work... but would you rather be fussing with dlopen?).  Annotations can be very useful as well -- see JAX-RS, for instance.

While some of the design is suboptimal in various places, in general it's quite usably designed.  And if you stay far away from JNI (Java bindings to native code), it will be considerably easier to diagnose issues, and thus to develop and maintain.

Re: my perspective, I tend to care about a lot about very complex algorithmic work on fairly decently sized data sets, and very little about desktop presentation.  From a PL perspective, I cut my teeth on Cartridge BASIC and have used to varying amounts and varying years-ago Pascal, Logo, C, C++, a tiny bit of MIPS assembly, Lisp, Prolog, SML/NJ, Perl, Java, SQL (PostgreSQL dialect), and PL/pgSQL.  With respect to general-purpose programming, I pretty heavily favor Java and Perl for practical reasons; and I write a fair bit of SQL and occasionally PL/pgSQL for my work.  For me, I only really turned my attention towards Java after close to twenty years of programming in other languages (most using the C/C++/Perl set), so I can't really speak as to how easily you might learn it without much experience in similar languages.

> 
any suggestions? should I (re)start with a different language ? (also like the idea of using whatever language with openGL over directX for portability) but bare in mind I'm trying to keep it simple for now.

:) Thanks

openGL?  Hm, I recall poking at it once and it being fairly low level; you may find it simpler to look at slightly higher-level frameworks.  A number of cross-platform engines already exist, e.g. Crystal Space.

---

### Post by V for Vincent on 2011-02-26
It's not really about the language. It's more important to learn about program design than syntax or low-level details, so I'd suggest something high level. Also, for learning, pick something that's well documented rather than something that boasts a lot of syntactic sugar. Java or C# or Python (2.x, for now) would fit the bill.

---

### Post by nvteighen on 2011-02-26
> **cguy said:**
> 
It may be dead simple to pick up (ie: one week MAX from zero to advanced skills), but its downside is that you will be concentrating on using Python specifics (lists, Python strings etc.) instead of concentrating on concepts that'd allow you to make a simple transition to any programming language.


On the contrary, Python drew its concepts from a lot of other languages...

> 
I recommend C.
The language itself is tiny, really. Learn to use its libraries (input, output, memory allocation and other commonly used ones) and you'll have a solid understanding of what programming really is about.


No, programming isn't about pointers... It's about creation solutions for a computable problem in a formal language. The C-specific features are there just because you sometimes need access to the computer's internals. Actually, 90% of the C code I've read could/should have been written in a higher-level language.

It's true that C is small, which makes it a joy to use, compared to uh... C++... But it quickly becomes a burden. Even using highly abstracted libraries like GTK+ or GLib, you'll be still bound to memory management and meta-feature tasks which are there just to make it possible to implement some feature (instead of straightly implementing the feature).

> 
Not to mention that you can use C anywhere: from microcontrollers to desktop applications to kernel development, on virtually any available platform.


Yes, but that you can use it everywhere doesn't mean you should use it everywhere too. The "C-specific" niche has been getting smaller since 1972 when it was created because the advance in performance has made true high-level languages feasible. I can understand why Ritchie and Kernighan used C and not Lisp to write UNIX: Lisp was there, but it ran at prohibitively low speeds, even in Lisp Machines that used Lisp as native language. Now we can run huge Python or Java applications without noticing any difference in speed with huge C or C++ applications, except in very specific cases (e.g., games). You know, nowadays the most runtime is wasted in waiting for input... which depends on the user's speed.

Ok, Python has its quirks too. Simula-style OOP (= C++, Java) taught straight from the beginning, though improved by the fact that Python is a dynamic language. The Python "Standard Library" reflects too much C-isms just because the official implementation is written in C (Compare it to the Perl core library and you'll see what I mean, and the official Perl is also written in C). There's the hard inmutable/mutable distinction... But in balance, it makes the kind of programming a beginner usually does much easier.

Obviously, if you want to write a kernel, use C, but what programming beginner will do that??

---

### Post by irrdev on 2011-02-27
If you are serious about programming applications, I don't recommend learning Python first. Python is very easy to learn, but it's more like the world's most advanced scripting language than it is a true programming language that can be compiled into an executable. C++ or C# are my recommendations. Java is no longer relevant for the desktop, although it is great for programming for mobile devices (Android) and large business networks. For C++, I'd recommend using QT for your GUI programming; it is much more flexible and powerful than GTK. For C#, your only two real choices are either Windows Forms or GTK#. 

If you are planning to program for websites, you can forget everything I mentioned above. PHP is definitely the way to go, although Java and Python are sometimes useful too.

---

### Post by Shadowstripe on 2011-02-27
I appreciate the responses.

I was employed doing web development and design for someone else while it was enjoyable I did want to try something different and for myself in my free time.  

as for the kind of programming I would eventually like to try make a game, but I agree with what ve4cib said and would like to test the waters a little first and see how things go.

I have done some reading since and found some sites calming both Java & C# to be slow compared to C++ anyone have any comments on the subject ? (they didn't go into detail on how much slower or anything)

C# and cross compatibility. Am I correct in thinking that Installing Mono on linux will allow basic apps compiled on & for windows to run on Linux ? 

Thanks again

---

### Post by ve4cib on 2011-02-27
> **Shadowstripe said:**
> I have done some reading since and found some sites [claiming] both Java & C# to be slow compared to C++ anyone have any comments on the subject ? (they didn't go into detail on how much slower or anything)

C# and cross compatibility. Am I correct in thinking that Installing Mono on linux will allow basic apps compiled on & for windows to run on Linux ? 

Thanks again

Java and C# (well, the entire .NET framework, including C#.NET) are partially-interpreted languages.  What that means is that when you compile the program the resulting binary file is *not* machine code that is executed directly by the processor.  Instead it is "byte code" that is run through a separate program (e.g. the Java Virtual Machine or JVM).  These byte-code interpreters are generally very fast, so unless you're doing some serious processing (e.g. 3D game graphics) you usually won't notice any significant lag.

C and C++ on the other hand compile directly to machine code.  There's no middle-man to interpret the compiled program, so they tend to run much more quickly.  High-performance programs tend to use C++ for exactly this reason.

For basic beginner stuff don't worry too much about what language is fastest, or what's used for the most things.  If you've never programmed before the most important thing to understand is how to think like a programmer.  Understanding the basics like iteration, conditionals, recursion, good data structures, etc... is much more useful than learning a language.  Once you understand the core fundamentals of good programming you can pick up new languages very easily.  The syntax is different, but the essentials are largely the same.


As for the Mono/GTK#/C# question... I've never tried running Mono programs on Windows.  So take the following with a grain of sald.

From what I understand you should be able to do it, assuming all the libraries are in place.  Specifically the Windows machine will need the GTK# libraries.  Otherwise GUIs won't work.

For basic terminal programs that use the standard .NET/Mono libraries you should be able to run them on either platform in theory.  For anything more complicated than that... I'm really not sure.  Worst-case is you can install MonoDevelop on a Windows machine (or possibly even under Wine) and recompile your programs on that platform.  That should be guaranteed to produce executables that will work on Windows.

---

### Post by alegomaster on 2011-02-27
I say C. It gives you the most choices after you learn it.

---

### Post by directhex on 2011-02-27
> **ve4cib said:**
> Java and C# (well, the entire .NET framework, including C#.NET) are partially-interpreted languages.  What that means is that when you compile the program the resulting binary file is *not* machine code that is executed directly by the processor.  Instead it is "byte code" that is run through a separate program (e.g. the Java Virtual Machine or JVM).  These byte-code interpreters are generally very fast, so unless you're doing some serious processing (e.g. 3D game graphics) you usually won't notice any significant lag.

Not to be pedantic, but nobody uses interpreters anymore. Both .NET and Java are usually pumped through a JITter, a Just In Time Compiler, which turns the bytecode into optimized-for-your-PC machine code when you run it.

---

### Post by ve4cib on 2011-02-27
> **directhex said:**
> Not to be pedantic, but nobody uses interpreters anymore. Both .NET and Java are usually pumped through a JITter, a Just In Time Compiler, which turns the bytecode into optimized-for-your-PC machine code when you run it.

Semantics.  The byte code is interpreted/converted/processed/translated/compiled during run-time into something the CPU can understand.  End result is the same, but the English terminology is different.

---

### Post by shawnhcorey on 2011-02-27
If you're interested in web development, then choose one of the scripting languages, Perl, Python, Ruby, or PHP.  But don't confine yourself to one language.  In the last web project I did I had to use HTML, CSS, Javascript, AJAX, Perl, and SQL.  The days when using just one language have long since past, if they ever existed at all.

If you want to learn assembler, go ahead, but I would download one of the Commodore 64 emulators and learn 6502 assembler.  It is a simple 8-bit CPU with a small number of registers and all the material you learn there is transferable to larger ones.

---

### Post by Some Penguin on 2011-02-27
Not semantics. JIT results in what was formerly byte code being compiled at run time, meaning subsequent usage of the same code (as is fairly common in actual non-trivial applications) does *not* require interpretation from byte code.  This is a substantial performance win, and has been in place for years.

In addition, there exist AOT compilers.

---

### Post by ve4cib on 2011-02-27
> **Some Penguin said:**
> Not semantics. JIT results in what was formerly byte code being compiled at run time, meaning subsequent usage of the same code (as is fairly common in actual non-trivial applications) does *not* require interpretation from byte code.  This is a substantial performance win, and has been in place for years.

In addition, there exist AOT compilers.

Sorry, I should have been more precise: "semantics for the purposes of this conversation."  Yes, you are certainly correct.  I was just defaulting to my academic lab demonstrator "hide the overly-complicated, not-for-beginners details behind a thin veil of obscurity for the purposes of expediency" mode.  The dangers of teaching second-year university students how to program...


As for the concept of learning multiple languages, I concur with that.  Learning one language is good, but it's not terribly employable outside of very focused areas.  Learning a variety of languages -- and understanding why they're different and what language works best for any particular purpose -- is a very good idea.

Start with something relatively simple and well-documented, and then start exploring.  For example, if you start with Java and you decide you want to dig deeper into lower-level stuff then try out C or C++.

---

### Post by shawnhcorey on 2011-02-27
> **ve4cib said:**
> For example, if you start with Java and you decide you want to dig deeper into lower-level stuff then try out C or C++.

I don't know about that.  Java is object-oriented and C is not.  Learn Java first and then having to maintain C would be like jumping into a cold lake in January.

If you want to learn object-oriented programming try Ruby.  If you want to prepare yourself for C, try Perl.

---

### Post by ve4cib on 2011-02-27
> **shawnhcorey said:**
> I don't know about that.  Java is object-oriented and C is not.  Learn Java first and then having to maintain C would be like jumping into a cold lake in January.

If you want to learn object-oriented programming try Ruby.  If you want to prepare yourself for C, try Perl.

I started off with Java and went straight into C after that and survived.  It's really not as big a jump as everyone seems to think it is.

Obviously you don't dive into C by translating a major object-oriented Java application.  You start off with the basics again -- Hello World, some basic I/O, and slowly get into memory management and pointers.  Then you can start playing around with more complicated programs once you've got the basics of the language down.

The fact that a lot of the syntax is very similar between the two languages helps the transition immensely.  And the fact that both are strongly-typed does make life a little easier.  Going from Python to C might be a bit harder, but Java to C is definitely doable.

---

### Post by cgroza on 2011-02-28
> **shawnhcorey said:**
> I don't know about that.  Java is object-oriented and C is not.  Learn Java first and then having to maintain C would be like jumping into a cold lake in January.

If you want to learn object-oriented programming try Ruby.  If you want to prepare yourself for C, try Perl.
Nooo, not perl, the syntax will kill you!

---

### Post by Simian Man on 2011-02-28
I'd recommend learning Python.  It is simple, widely used, and most importantly will teach you many styles of programming: procedural, object-oriented and functional.  C is a horrible choice because you will be fighting the intricacies of the language rather than learning programming in general.


> **foxmuldr said:**
> Are you wanting to be a developer, or a coder?  If you want to be a developer, then I would recommend learning Intel's x86 assembly (not the AT&T syntax).

Learning assembly and understanding the machine at its most primitive levels will give you a unique, fundamental understanding of why things work the way they do in a computer program.  You will see through operating systems, through applications, through any layers of interpretation, and directly to the raw "bones" of the machine.

In addition to what nvteighen said, learning assembly will NOT teach you how architecture works.  x86 assembly was designed back in 1972 and the way machines work now is *vastly* different than it was then.  Between the hardware and the assembly code that you think you have so much control over lies the operating system and the micro-architecture which does a lot of things that affect performance that are not visible in instruction set: it translates the instructions into micro-ops, rearranges the order of your code, renames registers etc.

If you want to learn cimputer architecture, learn computer architecture.  It is a very interesting field and will give you insight into how computers work.  However you can't learn it by programming in assembly on modern systems.  Also if your goal is to be a good developer, there are much more important things to learn.

---

### Post by shawnhcorey on 2011-02-28
> **cgroza said:**
> Nooo, not perl, the syntax will kill you!

Perl inherited its syntax from awk(1), sh(1), sed(1) and C.  If you're going to learn C, learn Perl first.

---

### Post by shawnhcorey on 2011-02-28
> **Simian Man said:**
> I'd recommend learning Python.  It is simple...

Sorry, like all modern languages, Python is not simple.  It has its idiosyncrasies, just like all the others.  You can't tell me that `array[2:4]` is simpler than `@array[2..4]`.


All modern scripting languages are the same.  It takes about a day to learn the basics but years to master them.  And when you throw in all the FLOSS libraries available for each, it will take most of your career to grok them.

---

### Post by CptPicard on 2011-02-28
> **Simian Man said:**
> C is a horrible choice because you will be fighting the intricacies of the language rather than learning programming in general.

I'm in general agreement, but not quite. C is just simply very basic; it's C++ that is the complex monster. The issue with C is that you learn the basic control structures' meaning in any other language too, but not anything else from C itself, which means you'll be out there on your own trying to figure out how to actually construct more complex systems.

---

### Post by cgroza on 2011-02-28
> **shawnhcorey said:**
> Perl inherited its syntax from awk(1), sh(1), sed(1) and C.  If you're going to learn C, learn Perl first.

I learned C++ straight from python and the C syntax and concepts are familiar to me.

---

### Post by PaulM1985 on 2011-02-28
Java is nice.  It is what I started with and it made moving to C# very very easy.

Paul

---

### Post by nvteighen on 2011-03-02
> **shawnhcorey said:**
> Sorry, like all modern languages, Python is not simple.  It has its idiosyncrasies, just like all the others.  You can't tell me that `array[2:4]` is simpler than `@array[2..4]`.


That's not the problem: you're talking about syntax, while the point is about semantics. In the case you mention, both are equally the same.

The thing is what a certain programming language offers as basic data structures, basic means of combination and basic means of abstraction (cf. SICP). And then, evaluating whether those three aspects in a specific language are appropriate for teaching *programming*: it's quite obvious that when learning your first programming language you're actually learning two things simultaneously: programming and the language itself.

So, what you need is something that emphasizes the programming part, because after that's done, learning languages will become more-or-less easier in time. But if you don't learn the general aspects correctly (the usual case: assuming language-specific features to be general programming concepts), you'll fail when learning any language. That's why a simpler language is better, because it helps focusing in what programming is about.

Personal anecdote: I myself started programming in QBASIC and Visual Basic when I was very young, but I quit it very soon. Only a few years ago I decided to start over again and I chose C as my "faux first language". Even though QBASIC/VBasic had taught me what loops, variables and basic control flow, I didn't know anything about abstraction, modularization or data structures... and C didn't help me a lot because I had to learn lots of stuff that were important just to make a program run on C, but weren't actually important for programming itself. To be honest, Python didn't help me much more; my turning-point was Scheme, actually... :P

---

### Post by GenBattle on 2011-03-02
> **nvteighen said:**
> That's not the problem: you're talking about syntax, while the point is about semantics. In the case you mention, both are equally the same.

The thing is what a certain programming language offers as basic data structures, basic means of combination and basic means of abstraction (cf. SICP). And then, evaluating whether those three aspects in a specific language are appropriate for teaching *programming*: it's quite obvious that when learning your first programming language you're actually learning two things simultaneously: programming and the language itself.

So, what you need is something that emphasizes the programming part, because after that's done, learning languages will become more-or-less easier in time. But if you don't learn the general aspects correctly (the usual case: assuming language-specific features to be general programming concepts), you'll fail when learning any language. That's why a simpler language is better, because it helps focusing in what programming is about.

Personal anecdote: I myself started programming in QBASIC and Visual Basic when I was very young, but I quit it very soon. Only a few years ago I decided to start over again and I chose C as my "faux first language". Even though QBASIC/VBasic had taught me what loops, variables and basic control flow, I didn't know anything about abstraction, modularization or data structures... and C didn't help me a lot because I had to learn lots of stuff that were important just to make a program run on C, but weren't actually important for programming itself. To be honest, Python didn't help me much more; my turning-point was Scheme, actually... :P

I guess in the end everyone has to start where they feel most comfortable. Some people will instantly click with structs and pointers and malloc in c, but other will appreciate the abstraction provided in languages like python and BASIC.

Personally i'm of that BASIC school of thought; I started programming in QBASIC in high school, and moved to visual basic and then Java/Delphi/C++. I even did some C programming at uni (embedded), but found it to be a very different case when programming for high level operating systems. For me, C is more suited to those bare-bones cases at the embedded level, but the majority of the hacker community seems to have a high level of C proficiency.

In the end, as we say in New Zealand; different strokes for different folks. Suck it and see what flavor works for you.

---

