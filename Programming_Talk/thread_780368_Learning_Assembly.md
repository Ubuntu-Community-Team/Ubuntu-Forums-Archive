---
title: "Learning Assembly?"
date: 2008-05-03
forum: Programming Talk
---

### Post by malfist on 2008-05-03
I have an interest in learning assembly, I've seen some really cool things done with it that I've though, hey I'd like to do that. I'm used to programming with high level languages though, like Java and C/C++, and when the job demands it PHP (and if you count it as a language, javascript).

Does anyone have any really good tutorial or suggestions? Books to buy, links to read, etc? Especially for people who are used to high level programming?

Thanks,
Malfist

---

### Post by dempl_dempl on 2008-05-03
Well, I only know of **Art of assembler**. 
I've learned from there. Not much fun, but there aren't many books about assembler  . Tougher the subject, fewer the books :)  .

Note: This book is only for real men ( and women ), who show no fear .
It comes in three volumes in totally 1800 pages    , and all of them are the good stuff, no fancy pictures or anything :)  .

You can get it legally for free in PDF format.

---

### Post by NathanB on 2008-05-03
Jonathan Bartlett's "Programming from the Ground Up"
[http://savannah.nongnu.org/projects/pgubook](http://savannah.nongnu.org/projects/pgubook)

Randall Hyde's "The Art of Assembly Language"
[http://webster.cs.ucr.edu/AoA/index.html](http://webster.cs.ucr.edu/AoA/index.html)

Dr. Paul Carter's "PC Assembly Language"
[http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

Linux-specific information, tutorials, examples, etc...
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

Nathan.

---

### Post by engla on 2008-05-03
I don't know any books, but I had this project that I thought was fun that required learning, reading and modifying some assembler code: Learning, really, how to implement a buffer overflow exploit. This is where you insert your own assembler code into a buggy program and gets it to run it. It was fun to try out and understand what it really is about with buffer overflow security holes.

---

### Post by dempl_dempl on 2008-05-03
> **engla said:**
> I don't know any books, but I had this project that I thought was fun that required learning, reading and modifying some assembler code: Learning, really, how to implement a buffer overflow exploit. This is where you insert your own assembler code into a buggy program and gets it to run it. It was fun to try out and understand what it really is about with buffer overflow security holes.

AlephOne's tutorial, I presume   ?  Yeap, that's a good place to start , too :popcorn:

---

### Post by pmasiar on 2008-05-03
Consider learning first a language with real pointers and no fancy objects to protect you from your mistakes, like C. C is in fact ASM with specific CPU instruction set abstracted away.

If you want to wander so close to metal, consider learning Forth: another language which lets you code close to metal, but build  incredible abstractions simply and quickly, and the only language I am aware of which lets you manipulate both parameter stack and return stack.

ASM is fine, but 80% of it is dealing with the quirks of the CPU architecture. Boring stuff. We have higher abstractions for a reason.

---

### Post by Npl on 2008-05-03
A good way to learn would be starting [with this MIPS-Tutorial]("http://chortle.ccsu.edu/AssemblyTutorial/TutorialContents.html"). If you got the basics with an easy architecture you can then change to the scary x86 Architecture by getting [Intels Processor Manuals]("http://www.intel.com/products/processor/manuals/").
When you got a basic understanding you can also get gcc to output assembly and see how your C-Code looks in ASM (you can also learn alot about how to write C-Code that can get optimized by the Compiler)

---

### Post by NathanB on 2008-05-03
> **dempl_dempl said:**
> Not much fun, but there aren't many books about assembler  . Tougher the subject, fewer the books :)  .

The same can be said about Linux!  So, 'assembly language' and 'Linux' are "pees of the same pod" so to speak.  Makes for a nice marriage.  :)

Migrating from a commercial OS to the "nothing hidden" Linux is beneficial because one can learn how the "under the hood" items work.  Then, you are not beholden to any "OS Gods" when you disagree with them about how you want the OS to behave.

Likewise, migrating from a high-level language to the "nothing hidden" assembly is beneficial because one can learn how the "under the hood" items work.  Then, you are not beholden to any "language Gods" when you disagree with them about how you want the language to behave.

Nathan.

---

### Post by pmasiar on 2008-05-03
> **NathanB said:**
> Then, you are not beholden to any "language Gods" when you disagree with them about how you want the language to behave.

But you need God's patience and time to make any program to work :-)

That's I prefer to use tools intended to be used by mere mortals: Python is I can get away with it, C for speed if I must, Java if forced to :-)

---

### Post by LaRoza on 2008-05-03
> **pmasiar said:**
> Java if forced to :-)

Since you are (were) using it for your job, do they force you? I could see it now, a bunch of people in cubicles coding in Java with guys with whips and tasers and the catwalks overseeing the operating.

As for learning hard-to-use languages, I have recently started using Brainfuck. It is so simple I got the entire language in a matter of minutes. However, it is not the easiest thing to use.

---

### Post by pmasiar on 2008-05-04
> **LaRoza said:**
> Since you are (were) using it for your job, do they force you? I could see it now, a bunch of people in cubicles coding in Java with guys with whips and tasers and the catwalks overseeing the operating.

In Cubicleland, they don't need whips. [Pink slips](http://en.wikipedia.org/wiki/Pink_slip_%28employment%29) are enough.

---

### Post by evymetal on 2008-05-04
To the OP: 

I would make sure that you know how a machine really works before using Assembly (but I'm not great at it so perhaps listen to others' advice first) - Read up on turing machines or register machines etc if you can't remember them - assembly is on quite a close level to them.

---

### Post by malfist on 2008-05-04
I'm taking electronic classes, so I know the basic basic stuff.

---

