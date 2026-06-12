---
title: "Is a python os possible?"
date: 2009-04-03
forum: Programming Talk
---

### Post by dodle on 2009-04-03
This is just a question out of curiosity.  I am in no way an experienced programmer.

Would it be possible to build an operating system from python alone?

---

### Post by damis648 on 2009-04-03
I could swear we had a thread about this somewhere...
...if I could only find it...
:popcorn:

---

### Post by Simian Man on 2009-04-03
Not from Python alone.  Even Linux uses a smattering of assembly.  You could write the good majority in Python, but it would be slow as hell.

---

### Post by SunnyRabbiera on 2009-04-03
Yeh you could probably code an entire OS in python but I can imagine it will be a snailspace OS.
I dare someone to program an OS in Klingon though :D

---

### Post by dodle on 2009-04-03
Why would it be so slow?

---

### Post by damis648 on 2009-04-03
I believe it is just the way the VM works for python. See the Python Wiki: [http://wiki.python.org/moin/PythonSpeed](http://wiki.python.org/moin/PythonSpeed)

---

### Post by Sorivenul on 2009-04-03
It would be something interesting to attempt after Google releases [Unladen Swallow]("http://code.google.com/p/unladen-swallow/wiki/ProjectPlan").

Read more [HERE]("http://arstechnica.com/open-source/news/2009/03/google-launches-project-to-boost-python-performance-by-5x.ars").

Still, as has been said, some assembly would be required... ;)

---

### Post by nmccrina on 2009-04-03
Well, python is actually written in c, meaning that a python function actually calls some c binary to do the dirty work. So the OS would still be written in C, but slower because of the extra layer of complexity on top. Of course, the code would be a lot simpler to read. :)

---

### Post by nmccrina on 2009-04-03
There are some similar projects, such as the JNode operating system (written almost entirely in Java, with some assembly). It is here [http://en.wikipedia.org/wiki/JNode]("http://en.wikipedia.org/wiki/JNode"). I even saw an operating system that was written in Haskell, bu unfortunately I lost the link. :D

---

### Post by shadylookin on 2009-04-04
No, though you could theoretically write a large part of an OS in python. It would probably be excruciatingly slow

---

### Post by samjh on 2009-04-04
> **dodle said:**
> Would it be possible to build an operating system from python alone?

No.

At present, almost all operating systems use at least some Assembly.  High-level interpreted or JIT-compiled languages have been used to write operating systems, but they inevitably require substantial portions to be implemented using Assembly or C.

There are not many programming languages that can be used to implement operating systems on their own.  Ada, C, C++, Pascal, PL/1 are used for such purpose, but even they require some Assembly, or the operating system is highly specialised and limited in use (ie. for avionics, robots, etc., not general-purpose operating systems like Linux or Windows).

---

### Post by dodle on 2009-04-04
I guess I need to study up on Assembly, since I don't understand what that is.

---

### Post by slavik on 2009-04-04
yes it is possible, if you have a python machine code compiler.

---

### Post by pmasiar on 2009-04-04
> **dodle said:**
> I guess I need to study up on Assembly, since I don't understand what that is.

That would be the worst approach. 

Of course depending what your goal is - you never bothered to mention that, so any advice is based on WAG.

Learning basic of Assembly is fine (try wikipedia as always), but trying to understand OS written in ASM will just slow you down. Is you want to understand how OS works, *much* better off you would be (after becoming decent C programmer) to start reading code of some simple OS designed to be understandable by students (taking OS design course), like Minix (btw that's what Linus did).

ASM is just way too low level. If you want to understand concepts of something, using efficient high-level language like Python makes you order of magnitude (or more) more productive. ASM makes you 2 orders of magnitude *less** productive than in C, trust me on that. :-)

And despite what people above said, OS in Python could be possible in the future. Now of course is not - Python is fast enough, in the niche where it is used speed is mostly not a problem, and work to improve it is underway. Untill recently Python (a volunteer project) did not have huge resources as Java or C# had, so precious resources were invested in more urgent areas.

But OS written in 99% in Python (like Linux is 99% in C) certainly *is* possible. Read about [http://en.wikipedia.org/wiki/PyPy](http://en.wikipedia.org/wiki/PyPy) - reimplementation of Python which includes compiler (Psyco) and JIT optimizer. PyPy is written in RPython, a subset of Python (which many too dynamic parts removed foe speed). 

Another approach could be to use [http://en.wikipedia.org/wiki/Cython](http://en.wikipedia.org/wiki/Cython) which generates C code.

Of course such OS in Python would be excellent learning tool (simpler to comprehend than Minix). 

Another area where Python might in the future replace static languages like C is in programming desktop. Even now, and even on such weak CPU like OLPC has, a big part of it's desktop (Sugar) is written in Python: 

[http://wiki.laptop.org/go/OLPC_Python_Environment](http://wiki.laptop.org/go/OLPC_Python_Environment)

---

### Post by slavik on 2009-04-05
another thing you could have is some ROM with a python interpreter in the same style as some computers in the 80s had BASIC.

While knowledge of assembly would be required, you are not at that point yet. You are at the point where you first need to understand basic os concepts (memory management, scheduling, etc.)

---

### Post by jimi_hendrix on 2009-04-05
> **Sorivenul said:**
> It would be something interesting to attempt after Google releases [Unladen Swallow]("http://code.google.com/p/unladen-swallow/wiki/ProjectPlan").


African or European?

and you are my hero if you make a python compiler/interpreter in ASM thats built into your kernel

---

### Post by Shin_Gouki2501 on 2009-04-05
my favorite C++ OS : haiku

---

### Post by samjh on 2009-04-05
> **slavik said:**
> another thing you could have is some ROM with a python interpreter in the same style as some computers in the 80s had BASIC.

There are processors like that for embedded Java: [http://www.ajile.com/](http://www.ajile.com/) and [http://www.arm.com/products/multimedia/java/jazelle.html](http://www.arm.com/products/multimedia/java/jazelle.html)

The same could be done for Python if there is demand.  "Demand" being the key point. :)

---

### Post by snova on 2009-04-05
Hmm... Python operating system, or Python kernel?

If you wanted to do the former, with plain old CPython, you could probably reimplement everything past init (first transition out of kernel space, I believe) and pretty much have a Python OS. Maybe begin with LFS.

But the kernel is another thing. You would either need a C runtime with bits of assembly, or a really flexible Python compiler to the point where you could essentially write C with a Python-like syntax. But you have to get down to metal eventually, and Python on its own doesn't accomodate for that all too well (maybe the compiler could? Additional built-in types or something).

---

### Post by pmasiar on 2009-04-06
> **snova said:**
> a really flexible Python compiler to the point where you could essentially write C with a Python-like syntax.

Like Cython mentioned above? :-) Or RPython?
 
> But you have to get down to metal eventually, and Python on its own doesn't accomodate for that all too well (maybe the compiler could? Additional built-in types or something).

Which types are in C and not in Python? You can model anything using byte arrays - the problem is efficiency, and you can get it via Cython.

So real problem is lack of effort - Linux is worth more than 1B USD of developer's time, even if redeveloping in Python/Cython will result in order of magnitude improved efficiency, it is still dozens of millions dollars worth of time. There is no need for such huge time investment in reinventing the wheel, so it is not **feasible**. But certainly it is **possible**, for a dedicated team of thousands of hackers with nothing better to do with their time :-)

---

### Post by Sorivenul on 2009-04-06
After much thought and searching I have discovered this:
[http://www.yeeeeee.com/2008/07/03/a-computer-running-python-operating-system/](http://www.yeeeeee.com/2008/07/03/a-computer-running-python-operating-system/)

---

### Post by Wybiral on 2009-04-06
> **Sorivenul said:**
> After much thought and searching I have discovered this:
[http://www.yeeeeee.com/2008/07/03/a-computer-running-python-operating-system/](http://www.yeeeeee.com/2008/07/03/a-computer-running-python-operating-system/)

I knew it was possible... You just have to have the Python properly integrated with the hardware.

---

### Post by pmasiar on 2009-04-06
Another possibility is to use different (non-Intel i86) CPU architecture, like [http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture) .

"ThumbEE provides a small extension to the Thumb-2 extended Thumb instruction set, making the instruction set particularly suited to code generated at runtime (e.g. by JIT compilation) in managed Execution Environments. ThumbEE is a target for languages such as Limbo, Java, C#, Perl and Python, and allows JIT compilers to output smaller compiled code without impacting performance."

Extremely smart architecture, i am glad someone is doing something to kill the abomination what is i86 CISC architecture. About time, too!

---

### Post by fiddler616 on 2009-04-06
> **pmasiar said:**
> 
So real problem is lack of effort - Linux is worth more than 1B USD of developer's time, even if redeveloping in Python/Cython will result in order of magnitude improved efficiency, it is still dozens of millions dollars worth of time. There is no need for such huge time investment in reinventing the wheel, so it is not **feasible**. But certainly it is **possible**, for a dedicated team of thousands of hackers with nothing better to do with their time :-)
Well I feel like in the same way there's a difference in complexity/cost between Linux and something like MenuetOS or Haiku, there would be a big difference in complexity/cost between PythonOS and a more mainstream OS.

---

### Post by Greyed on 2009-04-07
> **snova said:**
> Hmm... Python operating system, or Python kernel?

If you wanted to do the former, with plain old CPython, you could probably reimplement everything past init (first transition out of kernel space, I believe) and pretty much have a Python OS. Maybe begin with LFS.


This has been done, kind of, by [Pardus]("http://en.wikipedia.org/wiki/Pardus_%28operating_system%29").  They have replaced the init sequence with one written in Python.  I wish Ubuntu had looked at Pardus' init before deciding to reimplement the wheel yet again as it did all that Ubuntu was looking for in its replacement.

---

### Post by samjh on 2009-04-07
> **pmasiar said:**
> Another possibility is to use different (non-Intel i86) CPU architecture, like [http://en.wikipedia.org/wiki/ARM_architecture](http://en.wikipedia.org/wiki/ARM_architecture) .

"ThumbEE provides a small extension to the Thumb-2 extended Thumb instruction set, making the instruction set particularly suited to code generated at runtime (e.g. by JIT compilation) in managed Execution Environments. ThumbEE is a target for languages such as Limbo, Java, C#, Perl and Python, and allows JIT compilers to output smaller compiled code without impacting performance."

Extremely smart architecture, i am glad someone is doing something to kill the abomination what is i86 CISC architecture. About time, too!

There are already Java processors using ARM architecture, so it would be very interesting to see other processors with integrated support for high-level languages at hardware level.

> **fiddler616 said:**
> Well I feel like in the same way there's a difference in complexity/cost between Linux and something like MenuetOS or Haiku, there would be a big difference in complexity/cost between PythonOS and a more mainstream OS.

As I said earlier in the thread, OS written using high-level languages exist, but they are highly specialised.  It will be several years - probably decades - before we see any general-purpose OS written using those languages in the magnitude of Windows or MacOS.  Then there will be a very big revolution, like when Unix was ported to C from Assembly.

---

### Post by mmix on 2009-04-07
Yes, once upon a time, there was unununium os ( unununium.org : link is dead now)

IIRC, The project was canceled, the leader*(1) said the reason why the project couldn't goes on at their homepage. (But, i don't remember anymore)

JNode os that written in java, and there is jython ( python + java).

Even you can get the code from unununium os.

--
1: Phil Frost

---

### Post by HavocXphere on 2009-04-07
95% of the OS could be python...but writing the other 5% in python would kill the performance.

Besides...you need an interpreter to interpret the python. (Unless you use a custom hardware interpreter as suggested above)

---

### Post by CptPicard on 2009-04-07
Using "writing OS in language X" is a stupid benchmark... it's again the old low-level fallacy of "language is more powerful if it is closer to the hardware".

You write an OS in a language that compiles natively and lets you do hardware and memory access in a straightforward, bare-bones manner. C fits the bill well.

After the OS is done, you can write your other layers and apps in other languages. Python, among others, works nicely here. I really can't see what the exact benefit of OS-level code in Python would actually be, especially considering that the OS is just supposed to "be there" and not be constantly hacked at at source level. A lot of high-level code can already be JIT-compiled for native, so the OS/VM layering does not really come into play here.

One much more interesting issue would be a centralized garbage-collection service at OS level... now that would be something.

---

### Post by soltanis on 2009-04-07
[http://en.wikipedia.org/wiki/Lisp_machine](http://en.wikipedia.org/wiki/Lisp_machine)

I really do not see why not, if you could find/build hardware that ran an interpreter for the Python language.

---

### Post by CptPicard on 2009-04-08
It was reasonable back in the day to build hardware acceleration for Lisp because you really had performance to gain, and Lisp was such a profoundly more high-level language than anything available (it still is...)

Modern machines don't really need any of that, and that's why Lisp machines failed in the marketplace. And on the other hand, modern Lisp environments are very capable of compiling Lisp for your regular register machine. 

And if you look at your typical Lisp application... it compiles to native all the way and calls for runtime services in the environment's runtime lib. If some of that were available at the OS level, great. But it has nothing to do with the OS being or not being in Lisp, and we'd get nothing extra if it were :)

---

