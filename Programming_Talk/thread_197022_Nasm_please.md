---
title: "Nasm please?"
date: 2006-06-15
forum: Programming Talk
---

### Post by fireshell on 2006-06-15
Can anyone point me towards a programming guide for linux (ubuntu?) and nasm? Further more does anyone know how to give nasm apps a gui? (windows programmer, assembly fan and want to cross over)

---

### Post by Gustav on 2006-06-15
gui in assembler!?!?

I would program the gui in C or C++ and use inline assembler with that.

---

### Post by fireshell on 2006-06-15
thats a good point :$ im used to windows too much. not much experience with c/++ either. thnx for the wake up tho i still like my assembly

---

### Post by JasonMU on 2006-06-15
Hi - You might like this book: Linux Assembly Language Programming (Prentice Hall Open Source Technology) by Bob Neveln.  But it's for a first course in assembly so you might find it a little elementary.  However, it does refer to more advanced books, so maybe you could check it out of the library. Also, the author is a faculty member at some university and you could email him for some other references.

Jason

---

### Post by bieber on 2006-06-15
[http://www.unusedino.de/linuxassembly/index.html](http://www.unusedino.de/linuxassembly/index.html)

That's the most comprehensive resource I've ever seen.  Although if you're moving to Unix systems, I'd advise leaving Assembly behind.  I used to write Windows apps using MASM, and tried to learn Assembly for Linux when I switched to GNU/Linux.  The problem is that once you leave Windows, you leave the world of everyone's system being the same.  If you write something using Linux system calls for an x86 CPU in assembly, and someone comes along with a PPC processor, or they're using GNU/HURD or OpenBSD or Mac OSX, they won't be able to just recompile your app the way they could if you wrote it in C or some other portable language.

The other problem is that there really is no GNU equivalent to MASM (I'm assuming you enjoyed the use of .if, .invoke, and other such macros), and no real community to go to when you have problems.

---

### Post by fireshell on 2006-06-15
Thnx, and i didn't overuse the MASM directives so i should be fine. I just find using assembly on a personal basis helps my overall coding. That and its a challenge. To be honest I've never used c++ beyond a hello world program... Though that can wait :P. thnx for the resources pplz

---

