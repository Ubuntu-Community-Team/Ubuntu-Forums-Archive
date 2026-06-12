---
title: "C++ Programming Games (like Core War)"
date: 2010-04-13
forum: Programming Talk
---

### Post by AaronRGod on 2010-04-13
Hoy there, gang!

I'm looking for games like Core War or Robowar done in C++, where you create your own fighter object and then send it to do battle against opponents. Does anyone have any recommendations? 

Again, I'm not looking for tutorials on how to program games in C++, but for 'programming games' that are played with C++. The former is all I can find through Google. Wikipedia links to an external list of several hundred programming games, but there's no indication of which language each game works in.

---

### Post by km0r3 on 2010-04-13
> **AaronRGod said:**
> Hoy there, gang!

I'm looking for games like Core War or Robowar done in C++, where you create your own fighter object and then send it to do battle against opponents. Does anyone have any recommendations? 

Again, I'm not looking for tutorials on how to program games in C++, but for 'programming games' that are played with C++. The former is all I can find through Google. Wikipedia links to an external list of several hundred programming games, but there's no indication of which language each game works in.

There are currently *8.000 games written in C++ **reported*** on Sourceforge. Maybe you should check there.
[http://sourceforge.net/softwaremap/?&fq](http://sourceforge.net/softwaremap/?&fq)[]=trove%3A80&fq[]=trove%3A165

There are other software portals like freshmeat, ohloh, [put name here]...

Happy coding.

---

### Post by Some Penguin on 2010-04-13
I'm not sure that Core War-style games make all that much sense with mainstream non-interpreted languages.  I suppose you could dig up an emulator for an older processor and have people cross-compile for that, but it seems not worth the effort.

---

### Post by Tony Flury on 2010-04-14
The whole point of Core Wars was that it had a Virtual Machine, and a simplified instruction set, and a single shared block of memory, where the compete programs try to crash each other by making the other progam execute an illegal instruction (normally a zero byte instruction).

The virtual machine is there to execute the "programs" and catches illegal instructions etc, and keeps track of where the "programs" are in "memory", and what instructions they are running next - and all programs have full access to that memory, and can move (effectively can manipulate their own program pointers)

That is very different from a normal multi processing environment, where although the OS keeps track of where the progams are in memory, it deliberately segments the memory map so that one program can't easily crash another.

As "Some Penguin" said it makes no sense to try to make C++, unless of course you can write a C++ compiler which creates the simplified instruction set - good luck with that.

You could of course write a Core Wars virtual Machine (and maybe a GUI) etc in C++ - that would be an interesting challenge.

---

