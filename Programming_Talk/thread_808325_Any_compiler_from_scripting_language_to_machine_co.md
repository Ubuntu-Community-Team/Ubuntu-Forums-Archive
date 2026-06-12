---
title: "Any compiler from scripting language to machine code out there?"
date: 2008-05-26
forum: Programming Talk
---

### Post by pedrotuga on 2008-05-26
for the fun of it, I would like to give a try to program a computer from scratch, just to play a bit around with the hardware interfaces so I get a deeper knowledge of how it really works.

Now I did some (very little) assembly and C back at university. It was quite boring mostly because of the way the course was given.

I would of course like to start whith the basics, using basic text modes of the graphical device (screen) for output and the keyboard for input.

Now I can of course use C or C++ and compile it. But i kind of got used to scripting languages. Is there any compilers for any not so low level language out there?
I would like to target i386 architecture.

By compilers I mean programs that turn a computer language into MACHINE READABLE LANGUAGE. Bytecode output 'compilers' are not what i am looking for.

---

### Post by slavik on 2008-05-26
there is a Perl to C translator (I've never used it) ...

---

### Post by CptPicard on 2008-05-26
> **pedrotuga said:**
> for the fun of it, I would like to give a try to program a computer from scratch, just to play a bit around with the hardware interfaces so I get a deeper knowledge of how it really works.

Then you really need to write your own assembly by hand. The higher-level scripting language you're trying to turn into assembly, the more incomprehensible and uneducational the end result becomes...

---

### Post by LaRoza on 2008-05-26
> **pedrotuga said:**
> 
Now I can of course use C or C++ and compile it. But i kind of got used to scripting languages. Is there any compilers for any not so low level language out there?
I would like to target i386 architecture.

By compilers I mean programs that turn a computer language into MACHINE READABLE LANGUAGE. Bytecode output 'compilers' are not what i am looking for.

You can use freeze with Python if you really want to. However, scripting languages are not normally used that way.

---

### Post by pedrotuga on 2008-05-26
you didn't took in account in your replies that I want to compile an application that runs on an architecture, not on top of an operative system.

AFAIK freeze tools produce code that is dependent on operative system libs and stuff.

I would like to program a bootable application that doesn't deppend on any other software, at all.

---

### Post by LaRoza on 2008-05-26
> **pedrotuga said:**
> 
I would like to program a bootable application that doesn't deppend on any other software, at all.

Two words: C and Assembly (don't count the "and").

How to make a boot loader (first step for what you want): [http://www.osdever.net/tutorials/hello_btldr.php](http://www.osdever.net/tutorials/hello_btldr.php)

If you want a high level language for devices, check out Forth.

---

### Post by pedrotuga on 2008-06-16
> **LaRoza said:**
> Two words: C and Assembly (don't count the "and").

How to make a boot loader (first step for what you want): [http://www.osdever.net/tutorials/hello_btldr.php](http://www.osdever.net/tutorials/hello_btldr.php)

If you want a high level language for devices, check out Forth.

It turns out that man other languages can be used as long as one is able to reatch the compiled operative system from the bootloader.

Any more advice/links/information/whatever concerning the absolute basics of operative system development are welcome. Don't be shy. Thank you for the answers so far.

---

