---
title: "What is the best way to learn assembly?"
date: 2010-05-23
forum: Programming Talk
---

### Post by Quarg on 2010-05-23
I am new to assembly, and really like it. However, I have found tutorials to either veer off in a direction I'm not concerned about, be in a syntax I don't want, or go incredibly slow, so that I just lose interest - I'll forget things because they mentioned them a chapter earlier, but then apply them for the first or second time 50 pages later. So, thus far, I have learned by writing programs and seeing if they work, and reading the Intel Software Developer's manual. I have also read some of the Assembly wikibook. Is this a bad way to learn? does anyone know of a decently fast-paced tutorial/book that will teach me assembly?

---

### Post by km0r3 on 2010-05-23
These are great resources on the web:
[http://maven.smith.edu/~thiebaut/ArtOfAssembly/artofasm.html](http://maven.smith.edu/~thiebaut/ArtOfAssembly/artofasm.html)
A quite comprehensive collection:
[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/index.html)

Please ask your friend Google, too.

---

### Post by PrototypeAlex on 2010-05-24
I tutor an assembler paper at university, the lecturer of the paper set up a website that anyone can access, the only thing is that it is loosely based around the 8051 instruction set.

Here it is anyway

[http://www-ist.massey.ac.nz/gmoretti/159233/index.htm]("http://www-ist.massey.ac.nz/gmoretti/159233/index.htm")

---

### Post by nvteighen on 2010-05-24
> **Quarg said:**
> I am new to assembly, and really like it. However, I have found tutorials to either veer off in a direction I'm not concerned about, be in a syntax I don't want, or go incredibly slow, so that I just lose interest - I'll forget things because they mentioned them a chapter earlier, but then apply them for the first or second time 50 pages later. So, thus far, I have learned by writing programs and seeing if they work, and reading the Intel Software Developer's manual. I have also read some of the Assembly wikibook. Is this a bad way to learn? does anyone know of a decently fast-paced tutorial/book that will teach me assembly?

No, why would that be wrong? I'm also learning some x86 Assembly mainly because of curiosity (I don't think I'll ever use it, as I tend to write very high-level stuff) and doing it that way. Inductive learning ("Learn by doing") is the best way to learn programming... learn the basics and then learn the things that you need.

What I've noticed is that sometimes you have to use GAS ("AT&T") resources along with NASM ("Intel") ones because there's no complete guide for any of both (or at least, I haven't found it yet). The syntax is different (sometimes, very), but the concepts and way-of-things are pretty much the same as long as you're using Linux syscalls or calling libc. Moreover, you can also use Mac OS X and *BSD guides as long as you translate the syscall numbers.

---

### Post by NathanB on 2010-05-24
Lots of readily-available resources....

Jeff's book:  [http://www.duntemann.com/assembly.htm](http://www.duntemann.com/assembly.htm)

Randy's book & assembler:

[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/index.html)

[http://webster.cs.ucr.edu/AsmTools/HLA/index.html](http://webster.cs.ucr.edu/AsmTools/HLA/index.html)

Jonathan's book:  [http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

Paul's tutorial:  [http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

Linux-specific ASM resources:  [http://asm.sourceforge.net/resources.html](http://asm.sourceforge.net/resources.html)

Over a hundred tagged links here:  [http://delicious.com/Evenbit/](http://delicious.com/Evenbit/)

Hope that helps!

---

### Post by Quarg on 2010-05-24
Thanks for all of your suggestions. I have found 'The art of assembly' to be particulary useful, with it's from-the-ground up explanation of exactly what happens to certain bits when operations are performed. I now understand hex and binary better than ever before, and boolean logic makes much more sense. I will look into the other suggestions too. Thanks a lot for the excellent links

---

### Post by manzdagratiano on 2010-05-24
While all the assembly tutorials are good to use, the best way after you get a little hang of assembly language is also to convert a C++ program into assembly code at compilation using the -S option
```

g++ -S input.cc
```This will generate an assembler file input.s, and reading that shows the direct correspondence between C++ commands and the sequence of steps performed in the CPU to execute the same. This is how I learned most of my assembly programming in college.

---

