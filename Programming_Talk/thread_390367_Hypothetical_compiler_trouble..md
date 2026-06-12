---
title: "Hypothetical compiler trouble."
date: 2007-03-21
forum: Programming Talk
---

### Post by m_kylli on 2007-03-21
The way I understand it, it is like this:

In order to compile a compiler you have to use an already existing compiler.
So therefore you should be able to track the history of a compiler by finding out
witch compiler was used to first compile it and then witch compiler that compiled
that compiler and so on.

My hypothetical question is this: If some sadistic guy by some miracle gained a wish
(Alladin's lamp or some such) and decided to wish for every compiler in the world to
be irrevocably erased, no matter where it was stored, how long would it take for software
development to get back on track?

---

### Post by pmasiar on 2007-03-21
Erasing binaries only, or also sources? compilers only, or including kernel, all drivers, internet infrastructure? Including CPU microcode?

---

### Post by Wybiral on 2007-03-21
Long enough for someone to write an assembler from hex code...

Then write a compiler from assembly.

---

### Post by lnostdal on 2007-03-21
6 days?

---

### Post by monkeyking on 2007-03-22
[http://en.wikipedia.org/wiki/Bootstrapping_%28compilers%29](http://en.wikipedia.org/wiki/Bootstrapping_%28compilers%29)

---

### Post by m_kylli on 2007-03-22
> pmasiar said:

Erasing binaries only, or also sources? compilers only, or including kernel, all drivers, internet infrastructure? Including CPU microcode?

Binaries and sources, compilers only.

> Wybiral said:

Long enough for someone to write an assembler from hex code...

Then write a compiler from assembly.

And that would take how long without sources to refer to? Today a new compiler is often an improvement of an older compiler, not written from scratch.

> lnostdal said:

6 days?

Based on?

> monkeyking said:

[http://en.wikipedia.org/wiki/Bootstrapping_(compilers)](http://en.wikipedia.org/wiki/Bootstrapping_(compilers))

Thanks, that's a very good link. Though it mostly seems to verify that you need a compiler to compile a compiler.

---

### Post by lnostdal on 2007-03-22
6 days based on [http://en.wikipedia.org/wiki/Creation_according_to_Genesis](http://en.wikipedia.org/wiki/Creation_according_to_Genesis) .. of course; a joke

..starting from scratch (say all software libraries .. or heck; all software in general was deleted) might not be all bad if it did happen .. we carry a lot of baggage that we could get rid of now..

---

### Post by m_kylli on 2007-03-22
Regardless of our technological advances, humanity has not yet reached godhood. :) 
It was a funny joke though.

You're right about baggage though. I wonder how many unnecessary libraries we're still carrying around in the name of compatibility?

---

### Post by pmasiar on 2007-03-22
> **m_kylli said:**
> Binaries and sources, compilers only.

I agree with people who maintain popular myth that Python is an interpreter.... and I say: nothing happened, what is all the fuss about? Switch to Python and be done with it :-)

Now better guess (because Python compiles to bytecode, it would be wiped out too):

I would start with reimplementing Forth - it is easy to write in Forth and compile by hand. It should take less than  a day for an expert. While doing that, other Forth experts would write (1) Python bytecode interpreter (in Forth) and (2) Python compiler (in Forth, to bytecode). (3) start Python and bootstraping C compiler (and any other language you need), written in Python (4) start write tests to verify implementations. So at the evening of first day, we have Python compiler (running on Forth engine) and people can start running validation tests and debugging PyPy and PyC compilers. So in less than a week we have release candidates of any compilers people care to resurrect. Maybe little more for complicated monsters like C++, C# and Java. Thats in case anyone would care for them :-)

We can use huge parallelism allowed by time zone differences, working around the clock, many smart people knowing exactly what to do, and fact that (by your hypothetical situation) Internet and everything works OK.

---

### Post by m_kylli on 2007-03-22
A week? that sounds about right I think. Though we might be underestimating people. Then again, we might be overestimating them to. People might panic first, looking through all their old discs and mailing their friends and associates to check if they can find a compiler.

Anyway, who do you think will have a modern compiler ready first. The linux community, microsoft or someone else.

---

### Post by Ramses de Norre on 2007-03-22
> **pmasiar said:**
> I agree with people who maintain popular myth that Python is an interpreter.... and I say: nothing happened, what is all the fuss about? Switch to Python and be done with it :-)

Now better guess (because Python compiles to bytecode, it would be wiped out too):

I would start with reimplementing Forth - it is easy to write in Forth and compile by hand. It should take less than  a day for an expert. While doing that, other Forth experts would write (1) Python bytecode interpreter (in Forth) and (2) Python compiler (in Forth, to bytecode). (3) start Python and bootstraping C compiler (and any other language you need), written in Python (4) start write tests to verify implementations. So at the evening of first day, we have Python compiler (running on Forth engine) and people can start running validation tests and debugging PyPy and PyC compilers. So in less than a week we have release candidates of any compilers people care to resurrect. Maybe little more for complicated monsters like C++, C# and Java. Thats in case anyone would care for them :-)

We can use huge parallelism allowed by time zone differences, working around the clock, many smart people knowing exactly what to do, and fact that (by your hypothetical situation) Internet and everything works OK.

If I'm correct, most python libraries are written in C, so you'll need a compiler to compile those... And the python interpreter/VM is probably also written in C, C++ or some other compiled language.

---

### Post by pmasiar on 2007-03-22
> **Ramses de Norre said:**
> If I'm correct, most python libraries are written in C, so you'll need a compiler to compile those... And the python interpreter/VM is probably also written in C, C++ or some other compiled language.

Python is written in C - that is why is is relatively fast - it calls C libraries all the time. But libraries were preserved in our thought, just compilers went to bit heaven, no? Are you telling me, after that week of hacking, that you are changinf specifications? :-)  

If specs changed, we will need some more time of course. :-)

---

### Post by Wybiral on 2007-03-22
I would first write an assembler in hexcode. That would be pretty easy.

People write compilers in assembly all the time, I'm sure someone out there could do it.

I think with assembly and C you could start constructing almost all of the other languages pretty quickly.

---

### Post by YopY on 2007-03-22
It is true, back in the first days of computer programming, the founding fathers of programming did all the hard work so we didn't have to.

I believe that, as long as the general knowledge remains, it'll take a few months at most to start anew. I mean, it's basically a matter of working from the ground up again - from direct processor bits and bytes to simple built-in commands (on the chip itself), from there to a basic form of assembler, write a simple compiler, and basically just work your way up again.

The knowledge of the lower levels of computers is and pretty much always has belonged to only a select few though, highly intelligent / patient / insane professors at IBM and such, mathematicians who have produced enormous amounts of computer algorithms and theories without ever actually touching a computer, etcetera.

Right now, everything we program is based on what other people did before us. It would be interesting to figure out how we would do it if we had to do it all over again.

---

### Post by JoxBG on 2007-03-22
The hypothetical answer:

Easy, get a copy of the only surviving compiler from Gates. I'm sure he has this scenario covered. :)

---

