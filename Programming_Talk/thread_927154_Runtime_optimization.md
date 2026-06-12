---
title: "Runtime optimization"
date: 2008-09-22
forum: Programming Talk
---

### Post by pmasiar on 2008-09-22
Buried in [most recent flamewar](http://ubuntuforums.org/showthread.php?t=925607) was interesting discussion   started by pp. (post #45) as response to cb951303. I edited out IMHO irrelevant parts, feel free to exhume originals. 

[quote=cb951303]
good optimization, speed, simplicity(for C), OOP concepts(for C++), wide range of tools, popularity are some of that I think of right now.[/quote]

[Let's ignore cb951303's notion who considers "good optimization" if programmer (and not compiler) does it]

[quote=pp.]
by my purely subjective evaluation:
optimization: I was not aware that C++ actually did optimize the compiled code but are prepared to learn better if so. Java ought to win with respect to optimization with its optimizing JIT compiler.

speed: If speed of execution is meant, then Assembly ought to be fastest if you really go to the trouble of actually optimizing your code. If speed to market is your goal, then a great many other languages are better suited for almost every application domain.

simplicity: forth, assembly, lisp, REXX, Smalltalk are all structurally simpler than both C and C++.

OO Concepts: Smalltalk and Java are at least as solid and complete implementations of OO.

Popularity: long live Basic which presumably is much more popular than any of the professional and useful languages. Also, popularity is not an intrinsic property of a programming language, and it may be a misleading metric because it might be popular in spite of its intrinsic qualities. For instance and without meaning to imply anything: Windows is much more popular on desktop and laptop PCs than all other OSs combined. [/quote]

To which I answered
[quote=pmasiar]I mostly agree with you, just little nitpicking and extending on comments you provided, to get your mind some food to ponder:

pp.> optimization: ... Java ought to win with respect to optimization with its optimizing JIT compiler.

Java's approach to JIT compilation was "state of the art" 15 years ago. Since then, huge advances were made. As a result, static typing is not only not required: it hinders optimization, because runtime compiler has much better info about variable real type than programmer ever has. Of course lots of tricky work has to be done to handle it correctly, that's why Python community is so excited about PyPy project: Python compiler in (subset of) Python: next step would be JIT compiler, and it is substantially more productive (and fun) to write it in Python than in C.

pp.>simplicity: forth, assembly, lisp, REXX, Smalltalk are all structurally simpler than both C and C++.

it's great to see that there are people who know about Forth, which is IMHO forgotten gem: one of the most simple and still most powerfull languages ever imagined.

pp.> Popularity: long live Basic

Basic's popularity was based completely on platform: beginner-friendly language on first interactive time-shared OS with interactive source code editing and on-demand execution where 3-times weekly batch runs of punchcards were the norm. Even back then were better and more powerfull languages, like PL/1 - but not with interactive development platform.[/quote]

and I got PM from mod slavik, who wanted to continue the discussion but did not wanted to extract it from that thread - instead he gave me permission to start new thread using also his comments:

[quote=slavik]
Run-time optimizations ...
It's interesting that you think that run-time optimizations are much better than compile time optimizations.

Please consider that there is a keyword in C++ "inline" that would optimize simple getters and setters (and many other functions) during compile time.

Larry Wall also added optional types to Perl6 for that same reason. In a dynamic language where ints can spill over to bigint, you might want to tell the interpreter that a variable will never spill over into a bigint so that the interpreter can simply use a static type (without checking all the time if the variable needs to evolve into a bigint all the time there is an assignment statement to it) to speed things up.

Please keep in mind that run-time optimizations are much like virtual functions, there is a speed penalty.

Also, would it pay to optimize the following if statement away during run-time?

if (x == someval) { print "blah"; }

a comparison on the low level (in terms of microcode) is a subtraction and a conditional jump based on the flags set by the subtraction (but you know this already). In order to optimize something during run-time, you have to stop(pause) the program which might then force you to flush the cache (since you might be looking up some optimization techniques in the memory) and when you resume it, it might even slow down the program ...

Then there are languages that optimize things by not evaluating anything unless they have to, a good case of this is Haskell. In a language like Python or Perl when you do something like "x = 5", the exact type of x is known right after that statement, but in Haskell, the only thing it knows is that x has to hold and Integer. Only after you try to output the value of x (forcing Haskell to actually evaluation "x = 5"), it will then tell you that x is an Integer holding 5.

```

slavik@slavik-desktop:~$ ghci
GHCi, version 6.8.2: http://www.haskell.org/ghc/  :? for help
Loading package base ... linking ... done.
Prelude> let x = 5
Prelude> :show bindings
x :: Integer = _
Prelude> print x
5
Prelude> :show bindings
it :: () = ()
x :: Integer = 5
Prelude>

```
[/quote]

Yes, I believe that runtime optimizations are better, because JIT compiler can make them using real usage data, instead of poor programmer doing them by wild guess.

Anyone cares to share opinion?

---

### Post by CptPicard on 2008-09-22
You, Sir, are Correct.

---

### Post by slavik on 2008-09-22
I just want to point out that one of the main points I have (in what pmasiar quoted) is that if you optimize some code while it is being executed, you risk flushing the L2/L3 cache and introduce some cache misses. Also JIT is done before the program is run not while. I am pretty sure that there is no such thing as "run-time optimization" (where a program's code is changed in anyway while it is being executed).

EDIT: It is also possible for the programmer to optimize his own code simply by iterating through an array in a specific way that would allow the system to have no cache hits at all. I do not know if such a thing is doable today, but back in the 80s, you'd access arrays in a different pattern depending on whether you were using C or Fortran to be the most efficient. I am sure I don't have to tell you about drum memory, pmasiar. I am not an ungrateful whipper snapper. :)

---

### Post by pmasiar on 2008-09-22
> **slavik said:**
> if you optimize some code while it is being executed, you risk flushing the L2/L3 cache and introduce some cache misses.

possibly, but JIT compiler might be aware of such things - and optimize only the innermost loops.

>  Also JIT is done before the program is run not while. I am pretty sure that there is no such thing as "run-time optimization" (where a program's code is changed in anyway while it is being executed).

Your infallibility missed link to [Dynamic Languages Strike Back](http://steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html) talk which I posted before, but was too lazy to dig out without prodding from you. Thanks! It explains how exactly it is done, in runtime, and why. 

> It is also possible for the programmer to optimize his own code simply by iterating through an array in a specific way that would allow the system to have no cache hits at all.

what would be quite embarrassing waste of coder's time, don't you think so?

> I am sure I don't have to tell you about drum memory, pmasiar. 

No, [Story of Mel](http://www.cs.utah.edu/~elb/folklore/mel.html) is part of cherished folklore of the hacker tribe 8-) 

Although I never experienced drum memory myself, I do have warm memories about sweet noise of [ferrit core RAM](http://en.wikipedia.org/wiki/Magnetic_core_memory) when our PDP/11 exhausted 64K(!) of "fast" transistor memory and hit slower ferrits. 8-)

---

### Post by CptPicard on 2008-09-22
> **slavik said:**
> I just want to point out that one of the main points I have (in what pmasiar quoted) is that if you optimize some code while it is being executed, you risk flushing the L2/L3 cache and introduce some cache misses.

Well, you would assume that if you do some sort of runtime optimization, the result would stabilize eventually, or even pretty quickly, to some kind of good solution that is relevant to the statistically typical usage of the code. I really don't think that the solution would change much after converging -- in particular the usage of really critical parts (inner loops etc) is probably pretty consistent.

---

### Post by Wybiral on 2008-09-23
Runtime analysis can share insight into the code that the developer didn't even realize. Especially when the code might react to user input or some other non-deterministic environment. The runtime optimizations could, in theory, be much more tuned to the usage of the code than the author could have imagined (wrt memory, inlining functions, patterns in the program flow that can be replaced by more efficient patterns... etc).

---

### Post by Wybiral on 2008-09-23
> **slavik said:**
> Also JIT is done before the program is run not while. I am pretty sure that there is no such thing as "run-time optimization" (where a program's code is changed in anyway while it is being executed).

That's not true at all. JIT compilation isn't just a "before you run it" compilation, often times it's generating code as it runs. Look up tracemonkey, for instance (which optimized based on a tracetree of the running bytecodes). Or, since you enjoy a good C program, play around with GNU Lightning to see what JIT compilation is all about.

---

### Post by slavik on 2008-09-23
> **CptPicard said:**
> Well, you would assume that if you do some sort of runtime optimization, the result would stabilize eventually, or even pretty quickly, to some kind of good solution that is relevant to the statistically typical usage of the code. I really don't think that the solution would change much after converging -- in particular the usage of really critical parts (inner loops etc) is probably pretty consistent.
if you run java code through tomcat vs. /usr/bin/java, you will find that tomcat will be slower the first time around, the second time, however, tomcat will beat the pants of /usr/bin/java :)

java app servers are designed/configured to re-run the same code over and over again, whereas the standard JRE isn't.

EDIT: a question ... you say that run-time optimizations are better ... better than what exactly?
Why is it that academia places such a hard emphasis on "computers are fast, memory is cheap"? computers are not fast, and memory is not cheap when you have someone reading a stream one character at a time and appending it to a string in a language where strings are immutable (talk all you want about GC, it still needs processor time to run and has to effective stop everything else so that the memory is only changed by itself(the GC)).

---

### Post by dribeas on 2008-09-23
> **CptPicard said:**
> You, Sir, are Correct.

Give me a (select your preferred interpreted language) program able to distribute 500 CORBA data elements (6D vectors: 6 doubles, including serialization and deserialization) data elements at a 50Hz rate.

On most programs, runtime optimizations are better than compiler optimizations, but then again, you don't hold the only truth. The real truth I know is this: language wars are useless.

Notice that for real calculus python uses C coded libraries... does that sound a ring? The real optimization is time-to-market, where interpreted languages are really better than C/C++ but just don't try to fool people with a silver bullet, if (whatever your language is) were the silver bullet, then you would not need to fight this stupid flame wars.

---

### Post by CptPicard on 2008-09-23
> **dribeas said:**
> Give me a (select your preferred interpreted language) program able to distribute 500 CORBA data elements (6D vectors: 6 doubles, including serialization and deserialization) data elements at a 50Hz rate.

How hard is the rate requirement? May be doable in realtime Java and sufficient resources.

By the way, calling the languages the high-level language crowd has a preference for "interpreted" is slightly misleading. They are typically bytecode compiled (or even native compiled) with some kind of runtime environment library backing them (like SBCL).

Then again, realtime systems are a specific breed... I have never really been very impressed by counter-arguments from really restricted niches when considering merits of a language in general.

> 
On most programs, runtime optimizations are better than compiler optimizations, but then again, you don't hold the only truth.

Exactly, "on most programs", which is sufficient enough. Corner cases are corner cases. Even in your specific case, profiling information and optimization based on that will result in better performance, even though you were not running any optimizations while you're actually in production (which would admittedly interfere with timing requirements).

Your use case actually sounds so regular that runtime examination of code's behaviour would probably yield excellent results. Compiler simply can't know beforehand how actual running of your code will look like, unless you meticulously hand-craft it. Even then, profiling will yield information for you, the programmer.

> 
 The real truth I know is this: language wars are useless.

Actually, these so called "wars" (so called by people who would rather not discuss any of this) are very informative. They specifically tend to be between people who hold the ideas that there is either no difference between languages (everything subjective) or that it's all task-dependent, *or* that there really is a difference in the sense that when "characterizing a problem solution programmatically", some languages in general perform better, perhaps excluding very specific cases where there are well-defined *technical* special requirements...

> The real optimization is time-to-market, where interpreted languages are really better than C/C++

Actually, my argument has to do more with capacity to express abstractions, time to market is more pmasiar's pet point, but they are two sides of the same coin... good abstraction *results* in improved time to market (it's hard to imagine good abstraction actually being so hard on the programmer that productivity would be hindered).

>  but just don't try to fool people with a silver bullet, if (whatever your language is) were the silver bullet, then you would not need to fight this stupid flame wars.

Oh man, I was caught out!! Here is evil me posting, trying to intentionally lure people into believing that My Language is Teh Silver Bullet...

Come on. There is no silver bullet, but higher-level languages generally contain more silver. There really should ideally be no machine at all from the program's perspective (and strictly speaking, there isn't, even in assembler), there is only syntax and associated semantics that promise to produce results when evaluated. As long as that contract holds, the machine is not relevant, and in theory, not even observable from within.

I was just talking with Wybiral about his Lisp implementation (in Python), and referring to the initial point, I could equally well ask you to provide me with a continuation-passing style trampolined lazy-evaluated language in a few hundred lines ... it really isn't doable in C without writing the runtime. This is really very interesting stuff, as CPS-form is theoretically very fundamental as it completely generalizes control flow as there is no implicit fixed return point for a function -- did you know that your C compiler converts C into something similar to a CPS-lisp for optimization and processing before compilation, to get these static compiler optimizations that are so crucial? This can actually be -- and is -- done to any pair of compiler front- and back-ends.

Another great feature of trampolined CPS is that there is actually no stack at all. Tailcalls are free, and CPS often allows crazy speeds in co-operative multitasking applications.. it can beat the pants off threads.

This sort of stuff really is of much more generally important nature than some strictly limited "push bits on this particular CPU fast enough" problems.

---

### Post by pmasiar on 2008-09-23
> **slavik said:**
> you say that run-time optimizations are better ... better than what exactly?

than static compile-time optimization, obviously?

At runtime, you have **all** information from compile, **and additionally** runtime info from profiling. Did you bothered to read the link I provided? It is not something I discovered or even work on: I read about it and found it interesting, that's all. If I was smart enough to implement it, I would not be wasting time here in PT forum :-)

> Why is it that academia places such a hard emphasis on "computers are fast, memory is cheap"? 

Actually, it is not academia but pragmatic programmers who have deadlines :-) I am surprised what thesis themes of grad students are mentioned at the CompSci mailing list: Less than one a year even sounds interesting and relevant :-(

> computers are not fast, and memory is not cheap when you have someone reading a stream one character at a time and appending it to a string in a language where strings are immutable 

then don't use string what you need to reallocate but a buffer. get some classes in data structures :-) If input stream is slow, you have plenty of time to process and reallocate between characters.

> (talk all you want about GC, it still needs processor time to run and has to effective stop everything else so that the memory is only changed by itself(the GC)).

Not if you use reference counting for GC. CPU is fast enough that there is plenty of time to do lots of things between disk reads, trust me.

---

### Post by pmasiar on 2008-09-23
> **dribeas said:**
> Give me a (select your preferred interpreted language) program able to distribute 500 CORBA data elements (6D vectors: 6 doubles, including serialization and deserialization) data elements at a 50Hz rate.

Of course if task is CPU-bound, C wins. But most tasks are not: communication with external world is usually way too slow (web) that there is plenty of time to optimize.

> you don't hold the only truth. The real truth I know is this: language wars are useless.

So why you waste your time? :-)

I never said that I hold the only truth. But from my personal experience, I have different productivity in different languages, so at least for me, it does matter.

>  Notice that for real calculus python uses C coded libraries... does that sound a ring? The real optimization is time-to-market, where interpreted languages are really better than C/C++ but just don't try to fool people with a silver bullet, if (whatever your language is) were the silver bullet, then you would not need to fight this stupid flame wars.

It's funny how you use my own sounbites as arguments, distorted to the point I have to disagree :-)

"time to market" is argument against "speed kiddies" who consider C or C++ the only language worthy to solve any problem, "because code would run faster". Yes, some libraries are in C for speed - but many are not, and are fast enough. Also, Python started as niche hobby language, and developers did not had the resources to spend for runtime optimization, like Sun for Java or MSFT for .NET DLR. Only now, when Python become popular, are there resources to focus on runtime optimization, especially when the code to do it can be done not in C, but in substantially more productive Python (PyPy project).

Language flamewars are stupid for people who do not accept that there **are** differences between languages. As CptPicard said so eloquently, HHL have more silver in their bullets 8-)

---

