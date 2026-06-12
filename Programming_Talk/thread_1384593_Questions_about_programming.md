---
title: "Questions about programming"
date: 2010-01-18
forum: Programming Talk
---

### Post by Frogging101 on 2010-01-18
I am just beginning to understand programming, and I have some questions:

1. In the C programming language, how are things like 'printf', or 'scanf' made? How do those functions 'know' what to do? Who programmed those?

2. How are programs optimized for things like GPGPU, and how do things like raytracing in Blender happen? How are those things programmed?

I didn't ask many questions because I know when people reply, it will start a discussion, and I will have more questions.

---

### Post by Can+~ on 2010-01-18
Surprised that nobody has replied so far.

> **Frogging101 said:**
> 1. In the C programming language, how are things like 'printf', or 'scanf' made? How do those functions 'know' what to do? Who programmed those?

There are many levels involved. The thing is that each OS implements it's own way, and then is wrapped around with the standard C. So the reason why this things are portable, is basically because the same function definitions are kept.

If you want to understand even deeper, the OS is in charge of many things, including which processes enter de CPU (Scheduling), how to manage memory pages (Pagers and Swappers). The OS also has it's own set of libraries which are usually called an API, in this case, in the case of *nix, the OS API is POSIX. Then printf() and whatever function is declared as a function that calls the POSIX functions.

And if you still want to go even further (Assembly). You'll realize that I/O is issued at the processor level as interruptions, which causes the kernel to execute a certain piece of code belonging to the kernel space that does whatever action was requested depending on a registry argument (print to a terminal, read a file...)

So to answer your question, the Kernel programmers wrote the lowest-level things, the GCC guys built the libraries to wrap them, and you link to them.

> **Frogging101 said:**
> 2. How are programs optimized for things like GPGPU, and how do things like raytracing in Blender happen? How are those things programmed?

That's a whole different subject and out of my domain. Most things related to 3d graphics are known algorithms. Raytracing shoots a ray that bounce of surfaces and establishes the incidence of the light, the color, and many other aspects. How it's particularly coded, I have no idea.

---

### Post by c0mput3r_n3rD on 2010-01-18
Like Can+~ said, it really comes down to assembly.  If you want a good understanding of how computers work in general, I suggest learning assembly if you have to time (and it takes quite a bit of it).  MASM (Macro Assembler) is open source in both 16 and 32 bit versions.  If you have a 64bit processor you have to use 32bit programming, and if you have a 32bit processor you have to use 16bit programming.  I just took a college course in TASM (Turbo Assembly) and loved it.  Unfortunately there aren't too many free learning material out there (if any that are worth reading).

---

### Post by Zugzwang on 2010-01-19
> **c0mput3r_n3rD said:**
> Like Can+~ said, it really comes down to assembly.  If you want a good understanding of how computers work in general, I suggest learning assembly if you have to time (and it takes quite a bit of it).  MASM (Macro Assembler) is open source in both 16 and 32 bit versions.  If you have a 64bit processor you have to use 32bit programming, and if you have a 32bit processor you have to use 16bit programming.  I just took a college course in TASM (Turbo Assembly) and loved it.  Unfortunately there aren't too many free learning material out there (if any that are worth reading).

For completeness, I'd like to point out that I think there are multiple mistakes in this post. I don't think that the Microsoft Macro assembler is open source. Also, of course you can do 64-bit assembly for 64-bit machines and 32-bit assembly for 32-bit machines/OS. Both MASM and TASM don't support object files for Linux and don't run on Linux either (except in Wine or a dosbox).

---

### Post by wmcbrine on 2010-01-19
You'd be amazed at the amount of work set off by a simple printf(). Especially if you're using a graphical terminal. I started on trying to describe all the layers, but gave up.

But basically, printf() is a library function that takes the parameters you give it, renders them into the actual text to be output, and passes that to stdout. It's relatively simple in itself, especially if you ignore all the formatting stuff -- stdout is where it gets interesting. But that's part of the system, not actually part of printf().

Here's one example printf() implementation:

[http://www.sparetimelabs.com/tinyprintf/index.html](http://www.sparetimelabs.com/tinyprintf/index.html)

---

### Post by Frogging101 on 2010-01-19
I have another question now

How do you know what functions are in libraries such as zlib? How do you know how to use that in your program?

---

### Post by nvteighen on 2010-01-19
> **Frogging101 said:**
> I have another question now

How do you know what functions are in libraries such as zlib? How do you know how to use that in your program?

The best way to know is by referring to the library's API documentation. It's the best way to know how to use a library as it was designed... Other methods would show you information you aren't supposed to use and are only relevant if you intend to modify the library or similar.

---

### Post by lisati on 2010-01-19
> **Frogging101 said:**
> I have another question now

How do you know what functions are in libraries such as zlib? How do you know how to use that in your program?

I don't have an answer specifically related to zlib - I haven't actually used the library directly myself.

As others have indicated, there's sometimes no "easy" answer - there is often a lot involved. If you're lucky, people who make the libraries will provide documentation that will tell you what functions are available, and give some information on how to use them. All going well, it will be fairly easy to read and understand. Failing that, there's always places like the forums if if you have a specific question in mind.

edit: nvteighen beat me to it! 

afterthought: one of the core ideas behind building a library of potentially useful routines is that you are spared a lot of the work of figring out how to do stuff.

---

### Post by c0mput3r_n3rD on 2010-01-19
> **Zugzwang said:**
> For completeness, I'd like to point out that I think there are multiple mistakes in this post. I don't think that the Microsoft Macro assembler is open source. Also, of course you can do 64-bit assembly for 64-bit machines and 32-bit assembly for 32-bit machines/OS. Both MASM and TASM don't support object files for Linux and don't run on Linux either (except in Wine or a dosbox).

Yes, masm is open source, yes masm is for linux too.  I meant to say you just can't do 16 bit bit assembly on a 64 bit processor.  I also never said TASM can run on linux, it's not an open source program and only runs of windows.

Froggin, you can also just view the file and look at the functions, and most of them have comments in the file that you can also use.  Just think of it this way, a function is a set of instructions that have a label to be able to refer to it.  A library is a set of functions used to accomplish a task, and mostly to get the simple things like input and output taken care of.  You wouldn't want to write an stdio file every time you want to write a c++ program! They give you functions to use in order to do that.

---

### Post by lisati on 2010-01-19
> **c0mput3r_n3rD said:**
> Yes, masm is open source, yes masm is for linux too.  I meant to say you just can't do 16 bit bit assembly on a 64 bit processor.  I also never said TASM can run on linux, it's not an open source program and only runs of windows.

Froggin, you can also just view the file and look at the functions, and most of them have comments in the file that you can also use.  Just think of it this way, a function is a set of instructions that have a label to be able to refer to it.  A library is a set of functions used to accomplish a task, and mostly to get the simple things like input and output taken care of.  You wouldn't want to write an stdio file every time you want to write a c++ program! They give you functions to use in order to do that.

masm for linux? Must be a clone - I always thought "MASM" was "**M**icrosoft **AS**seMbler"........

---

### Post by c0mput3r_n3rD on 2010-01-20
> **lisati said:**
> masm for linux? Must be a clone - I always thought "MASM" was "**M**icrosoft **AS**seMbler"........


It is... but almost everything for windows works for ubuntu :)

---

