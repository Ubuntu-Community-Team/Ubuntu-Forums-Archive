---
title: "Creating/writing GUI with C?"
date: 2014-12-20
forum: Programming Talk
---

### Post by flaymond on 2014-12-20
Hello, since I wanna choose to learn C, I wanna ask if C can make GUI like calculator or mini-games? I found that Python has Tkinter library, but I don't know much if C have a library like that or you can write it directly without using those modules. C is created to write Unix, and Unix is CLI (in that time)..so I don't know. Is it available and possible?

---

### Post by TheFu on 2014-12-21
**Anything** that can be programmed can be accomplished with C.
Whether it is the best tool for any specific task/job is a different question.

There are many, many, GUI libraries.  If you like, you can use pure X/Windows (xlib) which has been around since the beginning of X/Windows or work at a higher level using Xm or Xt or any of the 50-ish other GUI libraries.  Many folks will want to use Qt or GTK.

Last time I wrote any pure X/Windows was in 1999. Generally, it just isn't worth our time to program at that level even if it is more efficient and takes fewer resources at runtime. Programmer time usually costs much more than the faster CPUs and added RAM needed by newer, higher-level, GUI libraries.

Both Qt and GTK have the added benefits of being cross-platform - so you can recompile and run on Windows too.  Of course, using pure X/Windows will let the program run on any UNIX-like OS with X/Windows.

For something simple like a calculator, using a scripting language would be more efficient in developer time, but also a good learning project for someone new to C (assuming you've already learned some C console programming).  

There are sticky posts at the top of this forum which explain how to learn many languages. Check those out.

---

### Post by flaymond on 2014-12-21
Thanks for your reply, that make me like "phew". I'm new to programming, and I don't experience any problem in programming in C till now (since that my interest and just start for 2 days). So, QT and GTK is cross-platform UI? That can make me write a program in Linux, than export it to Windows?

---

### Post by TheFu on 2014-12-21
> **InterProg said:**
> Thanks for your reply, that make me like "phew". I'm new to programming, and I don't experience any problem in programming in C till now (since that my interest and just start for 2 days). So, QT and GTK is cross-platform UI? That can make me write a program in Linux, than export it to Windows?

Yes, those are cross platform GUI libraries. Pick one.
No, you can't "export" a program to Windows. You'll need to get a toolchain for Windows (compiler and any libraries), move your code there and compile everything for that specific platform.  This is part of the reason why java and scripting languages are easier for cross-platform needs.  Compile/write once, run anywhere is NOT how C/C++ work. Every platform you want to run on needs to be recompiled. That takes time, skill, knowledge.  This is why programs compiled for 1 CPU type and OS do not work on others. The C is compiled into ASM for the specific CPU and knows how to be linked to other libraries on the same OS. libc is the main library for an OS - every OS will have a different libc, so for a compiled language, being compatible with that library and either the static version or the shared-object version is critical.

BTW, I was a cross-platform C/C++ developer for about a decade ... in the 1990s. Generally, writing in C just isn't smart from a developer productivity standpoint, unless the code needs to be for a real-time solution.  If absolute performance of the code matters, C is the language to use almost always.  There are times when perl might be better performing than C, but those are slim.  Other languages tend to be more efficient from a developer productivity standpoint. THAT is why perl, python, ruby are so great.  If I needed massive parallel  system support, the google languages - Dart and Go would be on my short list.

---

### Post by flaymond on 2014-12-21
Thanks for the advice! :KS

---

### Post by ofnuts on 2014-12-21
> **InterProg said:**
> Hello, since I wanna choose to learn C, I wanna ask if C can make GUI like calculator or mini-games? I found that Python has Tkinter library, but I don't know much if C have a library like that or you can write it directly without using those modules. C is created to write Unix, and Unix is CLI (in that time)..so I don't know. Is it available and possible?

Its all a matter of time. Writing a GUI app with a bare-bones C is possible, but it's like building your house starting with a forest of oak-trees and a hatchet. If you have never done it it is going to take a long while. With a library like GTK you get planks and two-by-fours instead of raw trees, and with C++ you get electric tooling (more efficient but requires some specific skills). If you use Java or Python TkInter it starts looking like a prefab house and Ikea furniture. Faster, but your options are more limited.

---

