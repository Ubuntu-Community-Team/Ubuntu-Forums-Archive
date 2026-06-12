---
title: "Debugging a C++ application"
date: 2015-03-02
forum: Programming Talk
---

### Post by calzakk on 2015-03-02
Can anybody recommend a debugger that *doesn't* use GDB? Are there any alternatives, or does it have a monopoly? Every IDE I've tried (Kdevelop, Anjuta, CodeBlocks, Kdbg) just cannot handle the application I'm trying to debug.  GDB crashes when I'm stepping through the code (whatever IDE I'm using). I haven't looked into this too much, because I've got a deadline to meet, but GDB is almost certainly the culprit. It's not a small codebase (100k LoC perhaps) and I'm using GCC 4.8.4 with a good sprinkling of C++11, but nothing too taxing (or so you'd think).

So instead of fully using Linux to develop and debug a feature for my application, I've now got to go back to *Windows* and use Visual Studio. When it comes to debugging C and C++ applications, Visual Studio will beat any open source alternative, hands down. I'm trying my hardest to move away from Windows, but I just can't commit fully to Linux and at the moment it looks as though I'll never be able to. I'm running Kubuntu with a virtual Windows machine, so I'm nearly there. But that final step is proving to be just too big, and I'm once again drawn back to Windows.

Sorry all, but I need to let off some steam. I've wasted far too much time with GDB :mad:

---

### Post by Matthew_Harrop on 2015-03-02
Good god man, what are you trying to debug?!

I don't mean to pry and if i am overstepping my bounds please say, but perhaps there is something in the way you have designed your program? Could it not be broken down into smaller pieces which are more easily debugged? 

Also, what is the specific cause of GBD crashing? Is it one or many things?

---

### Post by calzakk on 2015-03-02
> **Matthew_Harrop said:**
> Good god man, what are you trying to debug?!

LOL, not quite the response I was hoping for!

Basically, it's a shared object that's built from a number of libraries using SCons. There are also some testbed applications, and I'm debugging the .so via these.

Maybe I could try debugging one of the libraries separately. Some of them are fully independent, but some are dependent on others (like this one) so it might not be entirely straightforward, but I'll give it a try. Thanks for the suggestion!

When I'm using Kdevelop, I get this popup message:

[INDENT]Gdb crashed.
Because of that the debug session has to be ended.
Try to reproduce the crash with plain gdb and report a bug.[/INDENT]

It happens when I'm stepping through the code. A breakpoint fails to hit, and an assertion aborts the process. I'm trying to debug the code just prior to the assertion, but it's proving impossible to do because GDB stops stepping (and yes, the source code has all been fully built, nothing's out of date!).

I haven't had time to try out GDB yet; I've only briefly used it in the past, so it'll take a little time to make progress with it.

I might give DBX a try, just found it via a quick search. Can anybody recommend an alternative?

---

### Post by Matthew_Harrop on 2015-03-03
> I might give DBX a try, just found it via a quick search. Can anybody recommend an alternative?

Visual Studios? :P

Honestly, their stuff is brilliant. Its hard to take that from Microsoft, they know how to build development suites. 
I would try GDB by itself before you cast it off. I haven't had the opportunity to use KDevelop myself so I can't attest to its excellence and I haven't had such a large project that it causes GDB to crash so I'm in the dark as much as you are.

---

