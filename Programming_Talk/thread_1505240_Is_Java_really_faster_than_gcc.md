---
title: "Is Java really faster than gcc?"
date: 2010-06-08
forum: Programming Talk
---

### Post by donsy on 2010-06-08
I don't really know how to interpret these results because I don't know that much about the Linux "time" command. But here are the results of a hash calculation and table lookup over 133,784,560 iterations.

Java:
real    5m8.830s
user    5m6.123s
sys    0m0.404s

gcc:
real    6m10.449s
user    6m8.451s
sys    0m0.360s

As I said before I'm not sure how to interpret these results because the real and user times in Java are shorter than in gcc, but the sys time is longer. Can someone explain these results to me? I honestly don't see how Java can execute faster but it sure looks that way.

---

### Post by snova on 2010-06-08
> **donsy said:**
> As I said before I'm not sure how to interpret these results because the real and user times in Java are shorter than in gcc, but the sys time is longer. Can someone explain these results to me?

It means the application itself executed faster, but spent marginally more time in syscalls.

> I honestly don't see how Java can execute faster but it sure looks that way.

You'd be surprised. Implementation details may be related; perhaps Java's hash map is simply faster than the one you used in C. Perhaps its JIT produced better code than GCC did (did you compile the C code with optimizations enabled?). Or the JVM provided an advantage (e.g. freeing memory at odd times, but less often than repeated free() calls- purely speculation).

Lower level doesn't have to equate to faster.

---

### Post by Queue29 on 2010-06-08
Now try it with ```
java -server -Xms1024m [...]
``` and see if that's even better. (Replace the 1024m with as about as much ram as you expect your program to use)


And yes, Java can be and often times is faster than directly compiled languages, largely due to both compile-time and run-time optimization techniques made by the JVM that are unrealistic to implement directly by a programmer. Also, Java's garbage collector is extremely smart about rapidly used and forgotten- about objects, which likely gives it an edge in performance over cases where manual memory management handles everything case by case.


The age old myth of Java being slow is perpetuated only by grumpy old folks who [refuse to let go of their C compilers]("http://www.kerneltrap.com/mailarchive/git/2006/12/2/232033/thread").

---

### Post by DanielWaterworth on 2010-06-09
There's no reason a JIT compiled language can't be faster than a regular compiled language. JIT compilers have the advantage of being able to use run time information. For it to be quicker the speed increase of having run-time information has to outweigh the time it takes to compile. You ran many iterations so the speed increase will be large. This result doesn't surprise me, but you can't say as a blanket statement that Java is faster than C. Java is faster than C sometimes and C is faster than Java at other times. (All you can say is that Java is a memory hog and has awkward pauses when the garbage collector kicks in, not that I'm anti-Java or anything =P)

---

### Post by Tony Flury on 2010-06-09
It would be interesting to see what results would be with the same programs with the C compiled using the intel compiler (obviously on an intel chipset).

---

### Post by Milliways on 2010-06-09
The comments posted are all valid, but has it not occurred to anyone that the c code may not have been efficient. Java functions can be highly optimised.

I am also sceptical about simplistic benchmarks.
Back in the 1970s Dr Dobbs and Byte published benchmark tests for BASIC (then the only "high Level" language for microprocessors). I optimised the code in my BASIC to make the benchmarks run faster, but this didn't make any difference to most programs.

You can optimise any code, but once you have eliminated poor code, it just makes the program bigger, and uses more memory.

---

### Post by disabledaccount on 2010-06-09
> **Queue29 said:**
> 
The age old myth of Java being slow is perpetuated only by grumpy old folks ...
I see no reason for lower-level language to be slower than higher-level in any case (not talking about compiled object size). Besides, such comparisons have little sense to me, because effects depends on programmer skills, implementation of algorithms and target machine (f.e. ARM vs x86). Especially target machine is imortant, cause all RISC CPUs are optimized for C, not Java, PHP or C#.

---

### Post by Queue29 on 2010-06-09
> **tomazzi said:**
> I see no reason for lower-level language to be slower than higher-level in any case ... Especially target machine is imortant, cause all RISC CPUs are optimized for C, not Java, PHP or C#.

You clearly don't know what you are talking about. Programs written in C can't make run- time optimizations. And target machines are not "optimized for C". They run specific instruction sets, and it does not matter what language you use to compile down to those instructions. What matters is the compiler and the optimizations it makes relevant to that instruction set for the language you use, and in the case of high-level languages, what kind of VM is used. Of course, tiny things like micro-controllers can't run a VM anyway, so obviously C wins. 

Theoretically, C _can_ always be faster (by emulating high- level optimizations or otherwise), but in the real world, Java sometimes has an edge because we as humans can only comprehend so much optimized code.

---

### Post by trent.josephsen on 2010-06-09
Benchmarks are meaningless unless you post the code you used to achieve them and the compilation options.  Also, one data set is not statistically meaningful.

The First Rule of Optimization is "It's the algorithm".

---

### Post by Simian Man on 2010-06-09
The main thing is that it's easy to write efficient code in Java (and other high level languages) because common data structures and algorithms have high-quality, optimized implementations and the garbage collector makes very efficient use of memory.

In C it's much harder to write efficient code because you have to implement most data structures and algorithms yourself and manage memory yourself.  Many programmers feel that just doing it yourself implies that it's efficient, but **that's a myth**.  It's actually very hard to optimize these things yourself and very few programmers do a good job of it.

That's why for heavily optimized code C can win while, in reality, higher-level languages are usually more efficient.

---

### Post by Quikee on 2010-06-09
> **trent.josephsen said:**
> The First Rule of Optimization is "It's the algorithm".

No.. The First Rule of Optimization is "don't do it". :)

---

### Post by donsy on 2010-06-09
> **Queue29 said:**
> Now try it with ```
java -server -Xms1024m [...]
``` and see if that's even better. 

A 33% reduction in execution time, but more than double the syscalls:
real    3m28.029s
user    3m24.349s
sys    0m0.840s

---

### Post by trent.josephsen on 2010-06-09
> **Quikee said:**
> No.. The First Rule of Optimization is "don't do it". :)

Googled "rules of optimization" out of curiosity.  Didn't know about those. :lolflag:

---

### Post by disabledaccount on 2010-06-09
> **Queue29 said:**
> You clearly don't know what you are talking about. Programs written in C can't make run- time optimizations. And target machines are not "optimized for C". They run specific instruction sets, and it does not matter what language you use to compile down to those instructions.That is totally wrong. I suggest you should read at leaest one CPU's documentation, then express yours "what you're guessing-s"
All new RISCs are optimized for C - that means, the instruction set, the format of opcode, the way of creating stacks, way of creating relative jumps, and even number of application-level registers are selected to keep basic code snippets as fast as possible - fe. with minimal usage of stack. ARM is excellent example here - some C-snippets can be compiled into ONE asm instruction.

ASM can be slower than BASIC, f.e. because not every ASM programmer knows how to efficiently draw circles ;)

---

### Post by Axos on 2010-06-09
> **tomazzi said:**
> All new RISCs are optimized for C

What's sauce for the goose is sauce for the gander. There are good instruction sets and bad instruction sets. All well-written compilers and interpreters will benefit from them equally.

Not that it matters at all, but the Java runtime is written in C.

---

### Post by nrs on 2010-06-09
> **Queue29 said:**
> 
The age old myth of Java being slow is perpetuated only by grumpy old folks who [refuse to let go of their C compilers]("http://www.kerneltrap.com/mailarchive/git/2006/12/2/232033/thread").
Eclipse, Netbeans, ... just about every Java application do not help your assertion. :P I've seen it preform well or even better than C/C++ in certain specialized tasks but I've yet to see it really transfer over to desktop applications.

Just a personal observation.

---

### Post by soltanis on 2010-06-09
Let's not forget that Java is a pain to deal with.

---

### Post by disabledaccount on 2010-06-09
> **Axos said:**
> What's sauce for the goose is sauce for the gander. There are good instruction sets and bad instruction sets. All well-written compilers and interpreters will benefit from them equally.This is not so simple. The MAIN reason for dropping CISC architectures was that compillers are too stupid to select best solutions. My favorite CISC was M68k - it was easier to program in asm than in C ;)
Most currently used languages are derivatives of C and/or are written in C, and C was written in asm. 

The answer to question from title of this topic is:
Java **language** is not faster than C - but there are programmers who cant write good code - so there's corrective code inserted by compillers, mostly without their kowledge for saving their arses ;)

---

### Post by Simian Man on 2010-06-09
> **tomazzi]That is totally wrong. I suggest you should read at leaest one CPU's documentation, then express yours "what you're guessing-s"
All new RISCs are optimized for C - that means, the instruction set, the format of opcode, the way of creating stacks, way of creating relative jumps, and even number of application-level registers are selected to keep basic code snippets as fast as possible - fe. with minimal usage of stack. ARM is excellent example here - some C-snippets can be compiled into ONE asm instruction.[/quote]

Processors aren't "optimized for C".  That makes no sense because processors have no idea what C is.  They are optimized for the machine code that is frequently run on them and they are designed to be easy targets for compiler writers.  It doesn't matter if that code is generated by a C compiler or a Java JIT compiler or something else.  The things you mentioned as examples are all totally irrelevant to the source language.

[QUOTE=tomazzi said:**
> This is not so simple. The MAIN reason for dropping CISC architectures was that compillers are too stupid to select best solutions. My favorite CISC was M68k - it was easier to program in asm than in C ;)
Most currently used languages are derivatives of C and/or are written in C, and C was written in asm.

No, the main reason for dropping CISC architectures is because they were too damn complicated to create efficient implementations for.  Why do you x86-based processors use RISC like micro-ops despite the fact that compilers actually generate code for the CISC-like x86 instruction set?

> The answer to question from title of this topic is:
Java **language** is not faster than C - but there are programmers who cant write good code - so there's corrective code inserted by compillers, mostly without their kowledge for saving their arses ;)

That's not really it though.  Yes a good programmer can write efficient C code that can beat a higher-level language, but most programmers, even good ones, don't write that good of C code.  It's just too much work and isn't necessary for the majority of cases.

---

### Post by disabledaccount on 2010-06-09
> **Simian Man said:**
> 
No, the main reason for dropping CISC architectures is because they were too damn complicated to create efficient implementations for.Did I said something different?
> **Simian Man said:**
>   Why do you x86-based processors use RISC like micro-ops despite the fact that compilers actually generate code for the CISC-like x86 instruction set?...Beacause Intel invented cheap and crappy CPU that have been bought beacause of it's price only. Then, after some years there was just too much computers running x86 code to drop that crap where it belongs. Today, Intel have RISC processors that emulates crappy, ineffective and memory-hungry instruction set only because they still cannot drop that balast. Do you realise that?
And yes, I know that pipelines and threads leveraged Its computing power to very high level - but this can be compared to mow grass using advanced robot with scissors in his "hand" instead of mower.


> **Simian Man said:**
> That's not really it though.  Yes a good programmer can write efficient C code that can beat a higher-level language, but most programmers, even good ones, don't write that good of C code.  It's just too much work and isn't necessary for the majority of cases.Yes, I can agree - this is unfortunately common today, that we are wasting computing power and memory. I can imagine, that some day some High Skill Professional Programmer will tell the computer what it should do: "Listen, I will press Return key in a moment - be so kind please, and bind that action with placing newline character - okay?" :lol:

---

### Post by dwhitney67 on 2010-06-09
> **donsy said:**
> Is java really faster than gcc?
Yes.... wait no!  Here's proof...

Dammit... I lost that link.

Well, anyhow maybe Java is faster because it is Wednesday.

---

### Post by donsy on 2010-06-09
> **tomazzi said:**
> 
The answer to question from title of this topic is:
Java **language** is not faster than C - but there are programmers who cant write good code - so there's corrective code inserted by compillers, mostly without their kowledge for saving their arses ;)

Correct!!! I recompiled the C program with "gcc -O3 [...]" and here  are the results:

real    1m35.171s
user    1m34.706s
sys    0m0.068s

Compare these with the Java benchmarks above.

BTW I don't see how my code could have been THAT poorly written. After all, a  hashing algorithm involving bit-shifts, ANDs and XORs with the  result indexing into an array of integers is pretty hard to get  wrong. I suspect most of the optimization involved inlining the function  calls.

---

### Post by dwhitney67 on 2010-06-09
> **donsy said:**
> Correct!!! I recompiled the C program with "gcc -O3 [...]" and here  are the results:

real    1m35.171s
user    1m34.706s
sys    0m0.068s

Compare these with the Java benchmarks above.

BTW I don't see how my code could have been THAT poorly written. After all, a  hashing algorithm involving bit-shifts, ANDs and XORs with the  result indexing into an array of integers is pretty hard to get  wrong. I suspect most of the optimization involved inlining the function  calls.

Don't be shy... show us your C program.

---

### Post by donsy on 2010-06-09
> **dwhitney67 said:**
> Don't be shy... show us your C program.

You don't believe me? Oooo that hurts.

---

### Post by dtfinch on 2010-06-09
Add -fomit-frame-pointer and see if it drops another 5-10%.

A lot of the bigger performance differences IMO are style differences. Java sacrificed a lot of low level features in order to promote consistent, readable, extensible, reliable, secure coding style. You can write Java style code in just about any language, like C++, keeping the same performance costs that come with that style, or worse. Just like C programmers would try to port their code line by line to assembly, with no change in design, and find the performance no better than what was outputted by the compiler.

---

### Post by mmix on 2010-06-09
of course, some optimzed_non_human-assembly is better than human_c code.
[http://www2.java.net/blog/2008/03/30/deep-dive-assembly-code-java](http://www2.java.net/blog/2008/03/30/deep-dive-assembly-code-java)

---

### Post by donsy on 2010-06-09
> **dtfinch said:**
> Add -fomit-frame-pointer and see if it drops another 5-10%.


real    1m31.202s
user    1m30.606s
sys    0m0.072s

---

