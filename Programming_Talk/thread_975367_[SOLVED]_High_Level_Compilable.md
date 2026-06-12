---
title: "[SOLVED] High Level Compilable"
date: 2008-11-08
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-11-08
Ever since I started programming in C, I realized that compiled languages are very fast. But I also saw that to do things, that high level languages are capable of, is very difficult. So I began the search for a language that is high level like Python, yet compilable.

So far I looked at
[INDENT]
Lisp (compiles to byte code)
Pike (compiles to byte code)
Java (compiles to byte code)
[/INDENT]

Why is this? Is their a good reason for not having a compile to machine code option (not the only way of execution)? Are interpreted languages easier on the machine?

---

### Post by pmasiar on 2008-11-08
> **Mr.Macdonald said:**
> Why is this? Is their a good reason for not having a compile to machine code option (not the only way of execution)? Are interpreted languages easier on the machine?

Yes, **there** is a good reason not to worry about compilation: in most cases, speed does not matter much. If your app spends most time in library calls (database access, web server sesponse, waiting for user input), there is no much sense to spend much effort to compile the code - CPU is fast enough, and dynamic typing simplifies code **a lot**. And if speed does matter, often improving the algorithm (and possibly converting 5% of time-critical code into C library calls) is time better spent than writing whole app (including 95% of the non-time critical code) in a low-level language optimezed for execution speed.

But dynamic languages (with late binding etc), are often also compiled - just compiled for a virtual machine, not the actual CPU architecture.

---

### Post by Mr.Macdonald on 2008-11-08
their - there obviously I am not an English major

I understand that the execution speed of a interpreted program wouldn't change much but what about loading the script. In python's case it would have to go character by character and parse my file, then execute it

---

### Post by slavik on 2008-11-08
the 'official' Python implementation is written in C ... but that's besides the point. Parsing text is not as slow as you think.

---

### Post by LaRoza on 2008-11-08
> **Mr.Macdonald said:**
> In python's case it would have to go character by character and parse my file, then execute it

No, it does that once, then executes the byte code.

It works the same way everywhere. Binary is read beginning to end, executing the instructions are they are found. 

ELF is run on the OS, Python byte code is run on Python which runs on the OS. The OS runs on the hardware. 

Yes, this means speed suffers, to a degree. It really depends on the need for speed. If something requires speed, like a library for drawing 3d to the screen, or doing certain math, it would be best written in a language that is closest to the hardware (C, often times). These C libraries can be used in other languages, including Python. So if one uses C libraries for intense graphics and game engines, but uses a higher level language for the other aspects, you get the best of both worlds.

---

### Post by CptPicard on 2008-11-08
> **Mr.Macdonald said:**
> In python's case it would have to go character by character and parse my file, then execute it

Python has a bytecode compiler. You can easily see this by observing the compilation delay you get when you first run a Python script. On subsequent runs, it doesn't happen.

The SBCL implementation of Common Lisp actually compiles to native (and can produce rather interesting asm actually). The rest of the SBCL Lisp system is a runtime library that provides services to the native code.

Haskell is also compilable to native using GHC, and is a very high level language.

That said, yes, there are good reasons why some high-level language features make it hard to compile statically to native as the those features pretty much by definition rely on the ability to have very dynamic code "objects" in memory at runtime. There just simply isn't a way to know beforehand what they will be like, so you can't fix them in place using assembly. I'm pretty sure even Haskell actually embeds in the native binary some kind of minimal runtime environment. At least the bigloo Scheme compiler does this.

---

### Post by slavik on 2008-11-08
interpreting bytecode is fast ... very fast. not as fast as interpreting native instructions, but it is almost as fast. of course there are special cases, but they mostly hinge on design decisions.

---

### Post by CptPicard on 2008-11-08
Not to mention that bytecode can be JIT-compiled into native. Plus, into your bytecode format you can embed "hints" about what semantics you lost in compilation so that you can choose better compilation options (I am not sure if this is done anywhere but it's something I have considered myself).

I must admit I am rather fond of the SBCL style of compiling straight to native and then just having an extensive runtime library that the binary hooks into for services. It is one step away from turning those into system calls of the OS... *drool* :)

---

### Post by pmasiar on 2008-11-08
> **Mr.Macdonald said:**
> their - there obviously I am not an English major

Neither am I - and English is my forth language ;-)

> In python's case it would have to go character by character and parse my file, then execute it

Exactly like C: it needs to parse source first and compile it to binary. The difference is only that with C, binary is CPU-specific, while compiled Python code (.pyc files) are architecture independent and require presence of runtime support. Work is being dome on JIT compiler for Python, but it is not the huge priority (because it is not a huge problem). Google and NASA can use Python without compiler, chances are, it is good enough for you too ;-)

---

