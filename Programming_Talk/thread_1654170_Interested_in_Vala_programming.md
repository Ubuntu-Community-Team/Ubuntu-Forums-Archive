---
title: "Interested in Vala programming"
date: 2010-12-28
forum: Programming Talk
---

### Post by Quadunit404 on 2010-12-28
I had recently successfully compiled my first Vala application, WingPanel, and  I would like to know more about the language and how it works, especially compared to the language it's supposed to be an alternative to, C#.

I do understand it's a rather new language (it first appeared in 2006) and is still under development but what if I feel I want to add some more functionality to WingPanel? Right now it's rather lacking and doesn't show notification icons (beyond the ones in the indicator applet) or a calendar.

---

### Post by johnl on 2010-12-28
Off the top of my head, there are a few major differences:

1. C# compiles to .NET MSIL, bytecode which is executed by a just-in-time interpreter.  Vala is translated to GObject-based C, which is then compiled with gcc into native assembly.  

2. C# (.NET) includes a garbage collector, which at run time locates and frees out-of-scope objects and such.  Vala uses simple reference counting, which means that while there is no GC overhead, there are cases where the programmer needs to be aware of memory management and help it, using the 'unowned' and 'weak' reference keywords.

3. The libraries are completely differnet.  .NET includes a huge monolithic framework with almost everything you would ever need included.  Vala uses standard C libraries with a simple vala interface definition (.vapi file), in addition to a few standard vala libraries.



I dont know what WingPanel is, but if you are interested in making changes to it, just check out the code.  If you are familiar with C# the syntax should be pretty easy to make sense of.  The libraries will be completely different, of course.

---

### Post by Quadunit404 on 2010-12-28
WingPanel is a lightweight panel replacement being developed by the Elementary project written in Vala. Guess I should have stated what it is in the OP :wink:

And right now it's just 200 lines of Vala across multiple Vala source files, so there's not much functionality in it. I guess that if I learn Vala I can add more functionality to it.

---

