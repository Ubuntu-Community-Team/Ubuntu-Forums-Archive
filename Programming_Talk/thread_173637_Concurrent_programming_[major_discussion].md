---
title: "Concurrent programming [major discussion]"
date: 2006-05-10
forum: Programming Talk
---

### Post by draenor on 2006-05-10
Hey.

First off, I'd like to discuss pros and cons concerning a few of the major languages used today for concurrent programming. My goal is to get one step closer in seeing what today and tomorrow has to offer. 

I'll begin by stating my definition. 
> 
Concurrent programming is the simultaneous execution of multiple tasks performing the same computational matter including the technique of synchronization for doing so in possible parallellism. 


It doesn't necessarily have to be code executed in parallell, and unless it's a multicore processor, otherwise it's not physical parallell anyhow.

That said about concurrency, I'd like to state what I'm looking for.
> 
Since most of you know there are plenty of programming languages today, most related to each other one way or another. What I intend to find your opinion about, is what programming language today offers high performance parallellism for high end systems. 
- Real time systems in a time critical surrounding
- Effective I/O programming
- High performance run-time environment
- Mechanism for rendevouz, semantics, semaphores etc. 


10 Years ago, most major companies would have recomeded the sister language of vhdl commonly used in hardware achitecture today. That language would be [COLOR="DarkOrange"]Ada[/COLOR], because of it's powerful mechanism for serving multiple processess at once, or as java would call it, threads. 

Today I don't believe [COLOR="DarkOrange"]Java[/COLOR] is too commonly used because it's negative featues that the program has to be interptered in real time. Either way there are langueages which holds a much more neat way of serving request rather than the actionlistener object. 

[COLOR="DarkOrange"]c/c++[/COLOR] is probably the most common language today. Personally I don't know a whole lot about the powers of threading/multiple processess using either of theese languages, as I've been experience more programming here directed towards hardware. Any opinions on why c/c++ is better/worse than the other or possible not suitable at all would be interesting indeed. 

I've tried a relatively unknown language called [COLOR="DarkOrange"]MPD[/COLOR]. The advantage of this language is that it's almost a c-replica, and servers a really powerful rendevouz mechanism. The main disadvantages is that it's almost undocumented and not widely used at all today. 

Then there's always functional programming languages again. I've experienced a relatively new languages, [COLOR="DarkOrange"]Haskell[/COLOR]. Personally I tend to prefer the iterative way of programming. Either way I'm not sure there are great libraries for concurrency. 

[COLOR="DarkOrange"]Erlang[/COLOR] is yet another relatively new functional programming language developed by Ericsson. It's main purpose todays is to be the steering unit of everything from telecom switches to time critical applications for, let's say automobiles :). Yet again I see another functional language of which I don't find appealing enough. I know it holds a good mechanizm for pseudo-parallellism though. 


Enough with the ranting, I put the topic out there. Once again, what makes "language" the best choise for high performance parallell computation?
*This text probably contain a few mistypes and non-correct terminology, but that's not the topic here. *

---

### Post by RavenOfOdin on 2006-05-10
[QUOTE=draenor]
correct terminology
[/quote]

You're basically talking about SMP (Symmetric Multi-Processing) which on Linux gets us into device drivers and/or kernels - the former of which I've tried to learn about in the past and the latter of which is useful if you want to start developing.

[QUOTE=draenor]
[COLOR="DarkOrange"]c/c++[/COLOR] is probably the most common language today. Personally I don't know a whole lot about the powers of threading/multiple processess using either of theese languages, as I've been experience more programming here directed towards hardware. Any opinions on why c/c++ is better/worse than the other or possible not suitable at all would be interesting indeed. 
[/quote]

While it is a great language, I don't recommend C++ for threading because building threads on top of a C++ base would defeat the purpose of versatility with greater system interaction (greater than a language such as Java) at the same time. Some people like to do it, but I really wouldn't use it in my applications. If by any chance you're trying to use it for a network program, just stick with async sockets and save yourself some grief.

In my experience, C++ fulfills semantic requisites as well as those other things you stated. 

Oh, and if you're looking for a language which respects time constraints and is decent for hardware, learn ASM.

---

### Post by daneel_olivaw on 2006-05-10
Well Java solves it quite well, although not perfectly.. it uses a trade-off between Hoare and Hansen monitors, read [here]("http://java.sun.com/developer/Books/performance2/chap4.pdf") to see the differences. The imperfection is basically the reason why you have to wait for a synchronization condition "in loop" like here:
```
while (!condition) wait();
```

cause it's not guaranteed that the condition still holds by the time the thread gained control after having waited.

I don't know about C#.. I know it has more or less the same capabilities, but I prefer Java 'cause it's "purer" :P

And I don't know C++ almost at all.. so I can't do a good comparison; I can only speak good for Java.

---

### Post by rydow on 2006-05-10
I just want to add that language is just syntax. From both a programming and performance point of view the OS and the API is what is important. I mean if you look at C/C++ the concept of threads/processes are not even in the language but in the implementation of the libs interfacing the OS. In java and other interpreted languages you have these concepts buried into a virtual machine or interpreter, which in turn depend on which OS the software is run upon.

So IMHO the question of language is not the most relevant when discussing running things in parallel.

Cheers
J

---

### Post by LordHunter317 on 2006-05-10
[quote=draenor]That language would be Ada, because of it's powerful mechanism for serving multiple processess at once, or as java would call it, threads.[/quote]Careful.  Formally on most operating systems, code is excuted in processes consisting of multiple threads (potentially consisting of multiple fibers or an even further extraction).  When just talking about any stream of code excuted by a computer, I prefer the term 'thread of execution' to indicate that, since it could be a process, thread, fiber, async I/O callback, signal handler, interrupt handler, etc.  All of which potentially have the ability to execute in parallel with some other thread of execution.

Just to be clear so other people aren't confused.  Process and thread have strictly defined meanings and semantics on most platforms (and they're not constant across platforms, either).  You may have said terminology isn't important, but it really is here.

> It doesn't necessarily have to be code executed in parallell, and unless it's a multicore processor, otherwise it's not physical parallell anyhow.That's not true.  It's not *simulatenous*, but it is parallel.  Parallelism doesn't require the simulatenous execution of instructions between two seperate threads of execution.  It just requires that the execution of the two threads can be interleaved (i.e., TOE1 runs an instruction, then TOE2).

Usually, we want simulatenous execution, but it's not an out-and-out requirement.  All the problems of concurrent programming can occur with just a single processor.


> Today I don't believe Java is too commonly used because it's negative featues that the program has to be interptered in real time.Java source is never interpreted in realtime and Java bytecode is natively compiled ahead/just-in-time always.  Java is the most popular language in business today, in fact.

> Either way there are langueages which holds a much more neat way of serving request rather than the actionlistener object.Java supports far more expressive parallel concepts than that, including ones built into the API.  Several, in fact.

> Personally I don't know a whole lot about the powers of threading/multiple processess using either of theese languages, as I've been experience more programming here directed towards hardware.C and C++ threading is platform dependent.  It's totally different on VMS and Linux and Solaris and Windows.

[QUOTE=RavenOfOdin]You're basically talking about SMP (Symmetric Multi-Processing)[/quote]No, he's not.  Concurrent programming has nothing to do with SMP whatsoever, beyond the fact that some sort of SMP box is typically (not always) required to leverage the concurrency gains.

I/O-based systems may see huge gains without multiple processors.  CPU-bound applications like HPC will see gain reduction without multiple processors.

The rules and concepts of concurrent programming exist in almost total vaccum from the hardware they run on.  Even the implementations don't care, that much.  Otherwise, things like OpenMP would not be possible.

> which on Linux gets us into device drivers and/or kernels - the former of which I've tried to learn about in the past and the latter of which is useful if you want to start developing.No, it really doesn't.  Userspace parallel applications care about, at most (in the overwhelming majority of cases):[list][*]The number of processors on the system[*]Whether they implement SMT or not (e.g., P4's Hyperthreading)[*]On NUMA systems, the memory layout w.r.t. to each processor.[/list]None of those require particular care beyond how the kernel presents it's self, which is true of any syscall.

And that's a small minority of applications: many threaded applications don't care about any of those things, since performance may not scale linearly with CPUs, or the memory latency for being not local may not matter.

Parallel I/O servers like a web or FTP server generally care about none of those things, for example.  Things that do care would be HPC tasks like simulation, high-end databases doing OLAP (possibly OLTP, depending on the internals).

Even still, the details of the hardware implementation is quite abstracted to userspace.  NUMA on an Altix is treated the same way as NUMA on an Opteron in Linux, for example, even though the hardware implementations have no almost no similarities whatsoever.

> While it is a great language, I don't recommend C++ for threading because building threads on top of a C++ base would defeat the purpose of versatility with greater system interaction (greater than a language such as Java) at the same time.This statement makes no sense whatsoever.   What are you trying to say?  C++ doesn't provide grater system interaction than Java or even a more portable base than Java with the same featureset.  Java provides a standard GUI, standard networking facilties, standard threading facilities to just name a few.  C++ provides none of that.  So if that's what you're trying to suggest, your suggestion of 'using async I/O' is an instant non-sequitur, as that's platform dependent too.

But I don't understand what 'versatilitiy with greater system interaction' means, so please clarify.

>  Some people like to do it, but I really wouldn't use it in my applications. If by any chance you're trying to use it for a network program, just stick with async sockets and save yourself some grief.You cannot solve the C10K problem on any general-purpose computing platform without using threads.  It's impossible.  Threading must be considered for high-end parallel I/O applications.  Google for the paper if you do not believe me.  The fastest applications use some sort of edge-triggered notification (i.e., not select()/poll()) mechanism and multiple threads.

Apache 2 didn't move to providing a threaded MPM just for fun.  They did it because it is actually far faster.

---

### Post by draenor on 2006-05-13
> 
Oh, and if you're looking for a language which respects time constraints and is decent for hardware, learn ASM.

ASM certainly respects time constraints, but decent for hardware ? You get exactly the results you program for, and give it's low-level of implemantation I'd say you can you specify the optimal hardware settings. 
Either way ASM is not a real time choise, I am atm programming a few algorithms in assembler for the MIPS processor. Certainly it can be used to speed up some areas of an application, but this is not a programming language of where to write applications as a whole. 

> 
while (!condition) wait();

That's a perfect example of a java monitor. I have typed several programs using monitors for synchronization, but what really intrigues me is how well java threading implementation will last against a well written c-program performing the same tasks. Personally I haven't been able to provide a solid ground for testing efficency and quality difference between threading in java and c, but any pointers would certainly be interesting. 

The real question with java is, does the virtual machine provide good enough performance in a heavy computational threaded task as a c/c++ program? I understand the complexity of this question, since there are several different libraries in c based on the platform. But in general, it would be really interesting to see if java can match the c performance (or possibly the other way around). Any thoughts/ideas on this would be grately appreciated. 

LordHunter317, a great clarification of threading and parallellism. It's sometimes hard to keep phrases in it's exact sentence. Alot of the time what's going on inside ones head isn't always what comes out in the fingers end. What intrigues me is you how say java is the most popular language business wise. Personally on any platform I have only experienced a very very few programs written and developed in java (one of them being jedit, java text editor). Possibly I'm referring to the wrong category, but as far as I know most programs today are written in c* or vb, and that probably because of the performance boost of a program having all it's code already translated to machine code at compile time. 
You mention a few concepts not included in the java API. It would be exciting to review a few of those. If you wouldn't mind I would be happy to see a few links to concurrency libraries/concepts within java. 



Say a bank today, I doubt they would have a java implemenation on their servers. I don't know what they use, but my guess would definately that they're using a c implementation. Why is that then? Probably not because it's platform independent (which it's not), but because of the performance boost compared to a language such as java. 



Correct me if I'm wrong, but it seems there are typical usage examples for each language. 
1) The platform independent executing requests in parallell without the need for optimized performance. 
= Java

2) The high performance application that's not supposed to be operable between os's. 
= c/c++

3) The full effect of heavy concurrent computations 
= A functional language suitable for this. (name is irrelevant). 

4) The true concurrent application for true high performance systems (iterative programming, non asm). 
= ... I still haven't found the answer for this one, whats that MPM you mentioned?


There are probably some other good examples of use, and other languages specialized at it's area. Don't mind to share that information. Thanks :)

---

### Post by RavenOfOdin on 2006-05-13
> **draenor]
but this is not a programming language of where to write applications as a whole. 
[/quote]

I never said to write applications wholly in ASM code. Was there a subtext to my previous statement or an unknown user editing my post that I do not know about?  said:**
> 
2) The high performance application that's not supposed to be operable between os's. 


If you mean "portable" by "operable between os's" I beg to differ.

C++ can have a great degree of portability. Like you said in your answer regarding ASM, you program for what you get.  Unless you're dealing with MFC or, on the Linux end, certain socket and ioctl calls -- I really don't see a problem.

---

### Post by bboozzoo on 2006-05-14
[QUOTE=draenor]
1) The platform independent executing requests in parallell without the need for optimized performance. 
= Java

2) The high performance application that's not supposed to be operable between os's. 
= c/c++

3) The full effect of heavy concurrent computations 
= A functional language suitable for this. (name is irrelevant). 

4) The true concurrent application for true high performance systems (iterative programming, non asm). 
= ... I still haven't found the answer for this one, whats that MPM you mentioned?


There are probably some other good examples of use, and other languages specialized at it's area. Don't mind to share that information. Thanks :)[/QUOTE]
ad 1) Java is not performance oriented as far as parallelism is considered, it's portable yes, but nothing more

ad 2) This is where the posix standard comes in, I think it's precisely 4b which defines real time extensions, with 1003 being for threads and in general .1 for most calls related to parallel programming. If you take a look at different platforms, you find that linux, solaris, hpux (other posix systems? qnx?) are mostly posix compliant hence the code IS portable. Moreover, one should use facilities provided by system: round robin schedulers, priority levels, scheduler related calls (sched_yield...) etc. 

as for ASM, this is really a bad idea, unless you intend to implement your own mechanism of (timer interrupt)->(context switch)->(run in parallel) having in mind that someone has already done it (and possibly more bug free)

ad ADA) haven't really tried ADA for some time, however as ada can be compiled to machine code the issue as in case of C boils down to calling platform specific functions, hence unless you really need strongly typed language I would leave out ADA

and again if you're running a multiprocessor system, it's always better to have the operating system handle concurrency for you, from developer's point of view just stay with fork() or pthread_create()

as for parallelism I'am currently working on a compiler for Timing Definition Language, which generates C/C++ code handling at the same time selection of scheduler and priority assignment, thus the final bits can run in parallel

---

### Post by yaaarrrgg on 2006-05-14
Java has some annoyances, but I think it is often dismissed too early.

It's true that the original bytecode interpretors where slow, but newer JIT virtual machines (which can compile to native) are not that bad in terms of speed.  I was surprised to see java is actually pulling ahead of C++ in some  benchmarks:

[http://www.javaworld.com/jw-02-1998/jw-02-jperf.html](http://www.javaworld.com/jw-02-1998/jw-02-jperf.html)
[http://www.idiom.com/~zilla/Computer/javaCbenchmark.html](http://www.idiom.com/~zilla/Computer/javaCbenchmark.html)

Or if you want, you can use JET to compile java to native ahead of time.  I always assumed that Java would be slower C++, but now am not so sure.

Also, it looks like Java has a nice set of tools for concurrancy.  Java's libraries are not perfect of course, but many other languages have no comparable features:  

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/concurrent/package-summary.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/concurrent/package-summary.html)

---

### Post by LordHunter317 on 2006-05-14
[QUOTE=draenor]Personally I haven't been able to provide a solid ground for testing efficency and quality difference between threading in java and c, but any pointers would certainly be interesting. [/quote]I think you won't find a significant difference.  Java permits basically all threading and locking primitives to be implemented as native mechanisms, and they are on every JRE worth talking about.  The overhead is minimal at best and likely noise since the overhead of taking a lock is generally very large in the first place.

> The real question with java is, does the virtual machine provide good enough performance in a heavy computational threaded task as a c/c++ program?If you're CPU-bound and your code is clean, it may.  You can't implement SIMD on Java (well, a primitives library could be provided, but it wouldn't be faster) but until you get to that stage, you can be nearly as fast if you design your code correctly and carefully.  That means for most tasks, yes, Java is fast *enough*.

> What intrigues me is you how say java is the most popular language business wise. Personally on any platform I have only experienced a very very few programs written and developed in java (one of them being jedit, java text editor).That's because you don't see them.  They're running websites, performing server-side business logic, things of that nature.  It's mostly code you do not see or realize is running.

> Possibly I'm referring to the wrong category, but as far as I know most programs today are written in c* or vb,End-user applications?  Yes.

> You mention a few concepts not included in the java API. It would be exciting to review a few of those.Such as?  I pointed out simply that Java supports more locking mechanisms then you suggested.  It has native semaphores and condition variables, for example.  It didn't always, however.

> Say a bank today, I doubt they would have a java implemenation on their servers.Virtually every banking website on the planet is in Java or ASP.

> I don't know what they use, but my guess would definately that they're using a c implementation.C is barely used for web applications at all.  ASP (v 3.0) is the second most-used web application platform, but ASP.NET is on it's way to supplant it.

> 3) The full effect of heavy concurrent computations 
= A functional language suitable for this. (name is irrelevant). C or C++ with ASM is still the most common choice.

> 4) The true concurrent application for true high performance systems (iterative programming, non asm). See above.

> = ... I still haven't found the answer for this one, whats that MPM you mentioned?It's the threading model used by Apache.

[quote=RavenOfOdin]C++ can have a great degree of portability. Like you said in your answer regarding ASM, you program for what you get. Unless you're dealing with MFC or, on the Linux end, certain socket and ioctl calls -- I really don't see a problem.[/quote]Any GUI, you mean.  Or any advanced filesystem stuff.  Or any RPC/IPC mechanism.  C++ provides a limited about of portable functionality.

[quote=bboozzoo]ad 1) Java is not performance oriented as far as parallelism is considered, it's portable yes, but nothing more[/quote]As I noted, the Java standard allows for thinly-wrapped implementations of native constructs.  The overhead is minimal.

> 
ad 2) This is where the posix standard comes in, I think it's precisely 4b which defines real time extensions, with 1003 being for threads and in general .1 for most calls related to parallel programming.Which are abandoned standards.  And they were poor standards anyway, they didn't provide useful ways to determine enough things (e.g., default threading policy).

> If you take a look at different platforms, you find that linux, solaris, hpux (other posix systems? qnx?) are mostly posix compliant hence the code IS portable.But not performantly, which is what matters.

> 
as for ASM, this is really a bad idea, unless you intend to implement your own mechanism of (timer interrupt)->(context switch)->(run in parallel) having in mind that someone has already done it (and possibly more bug free)What are you talking about?  There is no context switch required to call assembly in any language compiled to native code.  They're all compiled to assembly before the executable is created *anyway*.

> ad ADA) haven't really tried ADA for some time, however as ada can be compiled to machine code the issue as in case of C boils down to calling platform specific functions, hence unless you really need strongly typed language I would leave out ADAUhh, C is strongly-typed, so this is a non-sequitur.

> and again if you're running a multiprocessor system, it's always better to have the operating system handle concurrency for you, from developer's point of view just stay with fork() or pthread_create()Which doesn't do nearly enough.  You can't just fork() as many times as you desire and expect optimum performance.

---

### Post by pharcyde on 2006-05-14
The biggest issue with concurrent programming is determining if any of the code you parallelize is worth the overhead of creating concurrency in general.  Context switches in some applications can be more trouble than they are worth depending on if they concurrency mechanisms are light-weight (internal threads) or heavy-weight (forks).  If the application doesn't at least gain a factor of 2 in performance its not even worth the effort in most cases.

As for languages, if it provides the necessary mechanisms to provide locks (monitors, semaphores, etc.) then it is a more reasonable candidate over others.  Java has some really useful libraries in place that provide most of the functionality needed for concurrent and distributed systems programming.  The boost library also has a useful library to do concurrent programming, but its not nearly as easy as threads and locks provided in Java.  I really don't prefer Java as a language over others in most respects for reasons i won't go into, but for developing concurrent and distributed applications it has to be one of the easiest languages to do it in.

---

