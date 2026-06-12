---
title: "Optimised code"
date: 2007-04-30
forum: Programming Talk
---

### Post by chriswyatt on 2007-04-30
This is merely trivial, but, I recently downloaded Swiftfox and was wondering how a program can actually be optimised for a specific processor.  Basically, I can't see how a program running on top of the OS can be optimised, surely its running on too high a level?  I'm not speaking with knowledge here, I don't know much about programming but I was just wondering.  Also, what sort of things are done to the code when it is optimised?

---

### Post by Mathiasdm on 2007-04-30
Well, the Firefox source code (a big bunch of text-files) is compiled into a binary (files that can be read by the computer) for i386 (meaning: any processor based on the i386 will be able to run it).
The 486 has had a few optimisations (for example: new low-level codes that are available.
Same with 586, Pentium II, Pentium III and so on.

If you have a new processor, you can take advantage of new (faster) instructions, so your program runs faster.
Another way of optimisation is what the compiler does: it takes the source code, turns it into Assembly code (which is basically is somewhat in-between high level languages and binary code -- yeah, I know, I'm simplifying). The Assembly code contains tons of very small instructions. It's often possible to optimise the code by deleting lots of unnecessary ones.

I hope that explains it a bit.

---

### Post by chriswyatt on 2007-04-30
Yeah, thanks, I sort of get it now.  I was thinking that the OS would do all the low-level stuff and the programmers wouldn't need to worry about it.  It's all very complicated stuff really, so, basically, programs don't exactly run completely on top of the OS, the OS just sort of holds it in place, so to speak :confused: .

---

### Post by tht00 on 2007-05-01
> **chriswyatt said:**
> Yeah, thanks, I sort of get it now.  I was thinking that the OS would do all the low-level stuff and the programmers wouldn't need to worry about it.  It's all very complicated stuff really, so, basically, programs don't exactly run completely on top of the OS, the OS just sort of holds it in place, so to speak :confused: .

I think you're confusing terms.

In the sense of the system, the kernel and OS combined handle the 'low level' operations that interface to the hardware.  The kernel does the hardware interfacing and generally, the OS(and extra software) has libraries available to to interface to the kernel.  This allows you to write code and when you need to interface to hardware, you don't have to write your own driver every time.

In the sense of programming, you can program with any language you like, high or low level.  As mentioned above, you don't need to worry about interfacing _directly_ to the hardware, but you can still write low level, step-by-step processor specific instructions. 

Depending on the language used, it may be able to be optimized (recompiled for that architecture) and get a decent speed boost and these would include traditional programming languages that compile down to machine-specific code (mostly C/C++).  Interpreted languages or those that use a virtual machine (various high level ;anguages) won't benefit from this near as much or at all (Python, Java, C#, etc).

---

