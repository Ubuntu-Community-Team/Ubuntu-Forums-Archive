---
title: "[SOLVED] Compiling Torque Game Engine gives an error about x86-64 instruction set"
date: 2008-04-15
forum: Packaging and Compiling Programs
---

### Post by noerrorsfound on 2008-04-15
I posted a thread on the Torque Engine forum, but since I haven't received a response, here you go.

I'm following the instructions here:
[http://eviwo.free.fr/torque/compile.html](http://eviwo.free.fr/torque/compile.html)

> make
--> Compiling lpng/png.c
**lpng/png.c:1: error: CPU you selected does not support x86-64 instruction set**
make[1]: *** [out.GCC4.RELEASE/lpng/png.obj] Error 1
make: *** [default] Error 2

**Edit:** I'm revisiting this old thread and providing this edit in case anyone ever wants to know the answer to this. According to users at the GarageGames forum, TGE does not compile under 64-bit.

---

