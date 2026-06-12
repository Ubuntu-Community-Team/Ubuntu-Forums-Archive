---
title: "C++ IDE for Heron"
date: 2009-10-02
forum: Programming Talk
---

### Post by xxguitarist on 2009-10-02
Tried a few the other day on my desktop. Can't remember exactly which version of ubuntu I have on there, but I imagine that whatever works on the laptop would work there too.

Tried geany, and liked the interface, but couldn't get the code to execute in the IDE, though it seemed to compile okay. 

Looking for a good, simple IDE- ideally with the ability to execute from the IDE. Highlighting etc are a plus.

---

### Post by TheStatsMan on 2009-10-02
> **xxguitarist said:**
> Tried a few the other day on my desktop. Can't remember exactly which version of ubuntu I have on there, but I imagine that whatever works on the laptop would work there too.

Tried geany, and liked the interface, but couldn't get the code to execute in the IDE, though it seemed to compile okay. 

Looking for a good, simple IDE- ideally with the ability to execute from the IDE. Highlighting etc are a plus.

You could try code::blocks

---

### Post by Zugzwang on 2009-10-02
> **xxguitarist said:**
> 
Looking for a good, simple IDE- ideally with the ability to execute from the IDE. Highlighting etc are a plus.

Assuming that you are interested in C and/or C++, I'd like to mention that I've recently written a tutorial for the KDevelop IDE featuring the basics of compiling, building and executing a program. KDevelop is relatively simple, especially when it comes to debugging.

It is here: [http://ubuntuforums.org/showthread.php?t=1258665](http://ubuntuforums.org/showthread.php?t=1258665)

---

### Post by kavon89 on 2009-10-02
Try NetBeans with the C/C++ Plugin.

---

### Post by originalsynthesis on 2009-10-02
> Tried geany, and liked the interface, but couldn't get the code to execute in the IDE, though it seemed to compile okay. 

I had to tweak it a bit to get it working. Do you have your terminal set up properly in EDIT>Preferences>Tools? The terminal field should say something like: usr/bin/gnome-terminal.

You might also check "Set includes and arguments", from the build menu, which tells geany what run commands to do on execute.

So far, geany is my fav, since I am just learning c++ and I really don't like wrangling with big IDE's when I just want to do basic stuff. Code::Blocks is nice, but it seems like overkill when you just want to learn how the language works.

---

### Post by xxguitarist on 2009-10-04
> **originalsynthesis said:**
> I had to tweak it a bit to get it working. Do you have your terminal set up properly in EDIT>Preferences>Tools? The terminal field should say something like: usr/bin/gnome-terminal.

You might also check "Set includes and arguments", from the build menu, which tells geany what run commands to do on execute.

So far, geany is my fav, since I am just learning c++ and I really don't like wrangling with big IDE's when I just want to do basic stuff. Code::Blocks is nice, but it seems like overkill when you just want to learn how the language works.


I checked my terminal location, and it was not correct, but I have corrected it and it still will not execute my program.

---

### Post by The Cog on 2009-10-05
Don't know about C++, but with C stuff in geany you have to menu Build before Execute. Compile makes the .obj file but Build makes the executable.

---

### Post by xxguitarist on 2009-10-07
> **The Cog said:**
> Don't know about C++, but with C stuff in geany you have to menu Build before Execute. Compile makes the .obj file but Build makes the executable.
That's the ticket! Strange that it doesn't show on the main toolbar next to compile & execute. 
Thanks!

---

