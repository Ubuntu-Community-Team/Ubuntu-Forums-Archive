---
title: "Just curious"
date: 2009-10-05
forum: Programming Talk
---

### Post by keygiwawah on 2009-10-05
I don't have a lot of experience with Linux as of yet...  But I was just wondering if anyone has written a Linux distribution in a different language than the norm or is it even possible.  All that I know about the source is that it is written in like C# or C++, or something in that family.

---

### Post by Renée Jade on 2009-10-05
The Linux kernel is written C programming language. The other programs that make up a "distribution" are written in a wide variety of programming languages. There are other UNIXs written in languages other than C, but the Linux kernel is the same for all distributions at a given time and it is only written in C (well, I suppose some small part of it must be written in something lower level than C, but that is all).

I'm no expert. People with more detailed knowledge please share :)

---

### Post by anagor on 2009-10-05
Linux is quite a broad term. There are numerous components that together make what most call Linux, or GNU/Linux for purists :)
Linux distribution is just a collection of the programs/applications, from different sources, bundled (packaged, hence the term packages in most distributions) together in a coherent way. 
There is in a nutshell:
kernel - direct to hardware interface, 
userland - all the programs that run on top of kernel and what a user actually sees and uses.
The same true for Windows and other Oses.

So, the kernel and it's modules are written in C/C++ .
The userland applications is written in any possible programming language there is.
In Linux most popular languages are: C/C++, perl, python, ruby, C#/Mono, Java, javascript. But you are free to use any programming language you see fit for yourself.

Again, the same true for Windows, for example:
Microsoft writes most of the windows kernel and userland in C/C++, however many parts of Office 2007 are written in C#/.NET.
The disc burning software you use may be written in Java, and the  bittorrent client in python.

Hopes it somewhat clarifies the things for you.

---

### Post by keygiwawah on 2009-10-05
> **anagor said:**
> Linux is quite a broad term. There are numerous components that together make what most call Linux, or GNU/Linux for purists :)
Linux distribution is just a collection of the programs/applications, from different sources, bundled (packaged, hence the term packages in most distributions) together in a coherent way. 
There is in a nutshell:
kernel - direct to hardware interface, 
userland - all the programs that run on top of kernel and what a user actually sees and uses.
The same true for Windows and other Oses.

So, the kernel and it's modules are written in C/C++ .
The userland applications is written in any possible programming language there is.
In Linux most popular languages are: C/C++, perl, python, ruby, C#/Mono, Java, javascript. But you are free to use any programming language you see fit for yourself.

Again, the same true for Windows, for example:
Microsoft writes most of the windows kernel and userland in C/C++, however many parts of Office 2007 are written in C#/.NET.
The disc burning software you use may be written in Java, and the  bittorrent client in python.

Hopes it somewhat clarifies the things for you.


Ya... Would it be possible to write the kernel in another language?

---

### Post by Calmor on 2009-10-05
> **Renée Jade said:**
> The Linux kernel is written C programming language. The other programs that make up a "distribution" are written in a wide variety of programming languages. There are other UNIXs written in languages other than C, but the Linux kernel is the same for all distributions at a given time and it is only written in C (well, I suppose some small part of it must be written in something lower level than C, but that is all).

I'm no expert. People with more detailed knowledge please share :)

I'd have to say you're pretty close from my understanding.  As for the kernel, C is chosen as it compiles to machine code very well, and can be much faster than a more abstract language if you know how to minimize processor cycles, etc.  Some could argue that the only thing closer to machine code is assembly language, but that's a bit less intuitive than C for most people.

As you said, there are programs written for Linux in all types of programming and scripting languages.  Most available languages have a compiler that will create working Linux binaries.

To the original poster who mentioned C# and C++, C++ is used in some libraries but (from my understanding) frowned upon in the kernel.  C# is implemented using Mono, but it's a .NET based language and requires a runtime environment (similar to Java).  I can't imagine it could ever be implemented in the kernel due to this.

Just curious, what are you looking to do?

---

### Post by Calmor on 2009-10-05
> **keygiwawah said:**
> Ya... Would it be possible to write the kernel in another language?

I'd imagine it's theoretically possible to write the kernel in any language that compiles directly to machine code.

That leaves out Java, any .NET language, and anything else that requires a runtime environment, unless you had a runtime environment that loaded up first (and was probably written in C or ASM).

---

### Post by anagor on 2009-10-05
Regarding the kernel itself, please see the wikipedia link:[http://en.wikipedia.org/wiki/Linux_kernel]("http://en.wikipedia.org/wiki/Linux_kernel")
Kernel consists of some 20 million lines of code, mostly written in very efficient C language, as this is among a very few languages that compiles efficiently and directly to a machine code.
So it will be almost impossible to write it in any other language.
Again, the same holds true for MS Windows, which is mostly written in C.

---

### Post by Renée Jade on 2009-10-05
The kernel is not written in C++ at all (see [http://www.kernel.org/pub/linux/docs/lkml/#s15-3](http://www.kernel.org/pub/linux/docs/lkml/#s15-3)).

You could write *a* kernel in another language, but it wouldn't be Linux anymore. But if you want to try and translate Linux into some other language and try and stay true to the original then go for it. But that would no longer be Linux. Linux is the kernel which is written in C and a little bit of assembly.

---

### Post by anagor on 2009-10-05
> **Renée Jade said:**
> The kernel is not written in C++ at all (see [http://www.kernel.org/pub/linux/docs/lkml/#s15-3](http://www.kernel.org/pub/linux/docs/lkml/#s15-3)).



My bad, sorry, wasn't focused enough when replied for the first time.

---

### Post by Renée Jade on 2009-10-05
Sorry for the redundancy. Everyone got in while I was writing.

I would think that some reasons why C is still used are that GCC has a good optimizer for a range of hardwares and, as has already been said, C complies to machine (i.e. it is a complied language, as opposed to an interpreted (e.g. bash) or semi-interpreted (e.g. java) language). C provides ease of use because it has high-level libraries, but it also provides low level control when you need it. Although some might argue that C++ also provides this high/low combo. Like I said,

[http://www.kernel.org/pub/linux/docs/lkml/#s15-3](http://www.kernel.org/pub/linux/docs/lkml/#s15-3)

is interesting. :)

---

### Post by Renée Jade on 2009-10-05
> **anagor said:**
> My bad, sorry, wasn't focused enough when replied for the first time.

No worries mate :)

---

### Post by keygiwawah on 2009-10-05
I just thought it was interesting that even though it seems very improbable of succeeding and would be very time consuming, that no one has done this... There are many people out there with nothing better to do, and do that kind of stuff all the time.

---

### Post by Reiger on 2009-10-05
Kernels can be written in &#8216;any&#8217; language so long as you have a basic &#8216;native&#8217; (opcode) VM (this need not be a very complicate VM, i.e. it need not be anywhere near as large as the Hotspot JVM) or so long the language of choice maps to opcode. (E.g. a lisp machine, java chips.) In a sense Linux too runs on top of a VM, namely its firmware/assembly components which do the lowest level hardware access the kernel needs.

The reason why C is still as popular it is likely has something to do with the fact that it is a very simple language yet has many, many libraries. This simplifies the task of getting something to just work.

---

### Post by forrestcupp on 2009-10-05
Like Reiger was saying, you can't write a kernel in C# or Java because they aren't truly compiled languages.  Java uses the Java Virtual Machine to kind of translate the code at runtime.  C# uses .Net to create byte code with Just In Time compiling.

But you could probably use any language that truly compiles to machine code to write a kernel.  The thing about it is that different languages are optimized for different things and some may compile more efficiently than others.  That's why kernel programmers usually use C or Assembly.

Aside from the possibility of doing it, you need to research into what it takes to write a kernel.  It has taken Linux 18 years to get where it is now.  [Since 2005](http://www.linuxfoundation.org/publications/linuxkerneldevelopment.php) there have been over 3700 developers from over 200 companies who have contributed to the Linux Kernel.  It's not just something you do because you have a lot of extra time.

---

### Post by ricegf on 2009-10-05
A Linux-like kernel with a complete userland was indeed written in another language - Ada, no less - in the late 1980's, funded by Intel and Seimens, and was available commercially for "mission critical applications" for a brief time. This was not exactly a smashing commercial success.

See [http://en.wikipedia.org/wiki/BiiN](http://en.wikipedia.org/wiki/BiiN) for the sordid details.

---

