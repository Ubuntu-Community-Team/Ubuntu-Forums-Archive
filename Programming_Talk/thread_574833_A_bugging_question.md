---
title: "A bugging question"
date: 2007-10-13
forum: Programming Talk
---

### Post by Drakx on 2007-10-13
OK

So this has really started to bug me now, if C is compiled to native code (machine code) and vb is also compiled to native code why is it that C is still faster then VB?

---

### Post by Martin Witte on 2007-10-13
vb (and also languages like python and java) dont compile to native code, it gets interpreted by a runtime engine, that's why programs written in those languages execute sometimes a bit slower.

---

### Post by Tomosaur on 2007-10-13
Added to Martin's point above - just because something is compiled to machine code doesn't mean it is done so efficiently. There are lots of ways to do things in machine code - finding the most efficient and fastest way is where the real skill lies. Your compiler may compile to machine code, but if the machine code it produces is bloated and inefficient, then your application speed will suffer.

Generally, good advice is to have your compiler spit out the assembly code, which you can then edit yourself to ensure maximum efficiency - although compilers such as gcc will generally produce very good binaries anyway. At the end of the day, the compiler is stupid, and only really makes a 'best guess' as to what machine code to output. If your application is speed-critical, you should probably check the assembly code to iron out all bottlenecks.

---

### Post by DMills on 2007-10-13
IMHO, but best practise is absolutely NOT to hand hack the compilers output **unless** you have demonstrated by profiling that you know exactly where the bottleneck is (And cannot find a better algorithm, which is usually the correct answer).

Hand hacking assembler is always the last resort (And even then you normally do better to start from scratch rather then from compiler output).

Regards, Dan.

---

### Post by cwaldbieser on 2007-10-13
> **Martin Witte said:**
> vb (and also languages like python and java) dont compile to native code, it gets interpreted by a runtime engine, that's why programs written in those languages execute sometimes a bit slower.

VBScript is interpreted.  VB6 code can be compiled into an executable.

---

### Post by mjwood0 on 2007-10-13
> **DMills said:**
> Hand hacking assembler is always the last resort (And even then you normally do better to start from scratch rather then from compiler output).

You also have to realize that there are some things that MUST be written in assembly.  Regardless, assembly really isn't all that bad in some instances. 

I agree 100% with your statement when it comes to desktop applications.

---

### Post by Wybiral on 2007-10-13
> **DMills said:**
> IMHO, but best practise is absolutely NOT to hand hack the compilers output **unless** you have demonstrated by profiling that you know exactly where the bottleneck is (And cannot find a better algorithm, which is usually the correct answer).

Hand hacking assembler is always the last resort (And even then you normally do better to start from scratch rather then from compiler output).

Regards, Dan.

I can actually think of a number of instances where I've seen GCC produce less efficient assembly then I could think of myself. I do agree that profiling is essential, and that as good practi_c_e you should avoid messing with the assembly (in serious projects, I enjoy it for fun but I wouldn't let it touch one of my real projects).

I also agree that 99.9% of the time the bottleneck has an algorithmic solution, low-level optimization only gets you so far.

But I disagree that it's better to start an assembly project from scratch. Compiler output is usually pretty well structured, labeled, and efficient (C code is, obviously C++ isn't practical to port to assembly). It usually makes a really good template.

But yeah, don't use assembly unless you're writing kernel level code or just goofing off. It's unmaintainable, hard to debug, and considering the rapid pace of hardware evolution it will render itself useless in a year or so (not to mention it's lack of portability even between modern computers).

---

### Post by pmasiar on 2007-10-14
I understand that you are concerned about efficiency, but as it was mentioned before, measure before you optimize. 

Ie if your code is web-based front-end for a database, about 80-90-95% of your total run time is spent in web server and database access. Even if you can still kill your code by bad design, any reasonable decent Python code will be about as fast as the fastest C code you can hack. Of course C might use little less resources, but that is important if your server is heavily used. meanwhile, you will create your code in Python 10 times faster, and it would be 10 times easier to maintain, fix and enhance.

Programming is engineering: it is about cutting corners to make things done. And you need to know what exactly are you doing and which corners you can cut. :-)

---

