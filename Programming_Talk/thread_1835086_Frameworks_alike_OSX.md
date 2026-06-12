---
title: "Frameworks alike OSX"
date: 2011-08-28
forum: Programming Talk
---

### Post by ahso4271 on 2011-08-28
Hi
I need to compile a MAC app on Linux which uses frameworks and therefore seems to miss lots of headers etc. 
Is there something alike or hints on how to deal with such.
Thanks

---

### Post by schauerlich on 2011-08-28
What application is this? Just because OS X and Linux are both Unix based does not mean that programs written for one will always work on the other. This is especially true if GUIs are involved. OS X has X11, but Linux does not have a replacement for Cocoa. The GNUstep project is a step in the right direction, but it is nowhere near being a drop-in replacement. You can try compiling it with GNUstep, but honestly it will probably be a waste of time.

---

### Post by ahso4271 on 2011-08-29
Gnustep seems very promising for future cross platform development, but for now I only do a x-plane plugin without gui. 
Ok so it uses lua, luajit, curl, bullet etc. Now on Linux i get lots of missing #include so i believe this is because on OSX the author has used frameworks. I'm not sure about, and new to osx->linux dev. but i wonder how to approach such on linux. I've added #include on linux as standard Unix approach but now I ran into tons of "multiple declaration of..." So i suspect osx frameworks to do special things with #include?
Many thanks for help/hints.

---

### Post by ahso4271 on 2011-08-29
anyone wanting to have a look:
[http://www.x-plugins.com/gizmo/downloads/Gizmo-11.5.25.tar.bz2?attredirects=0&d=1](http://www.x-plugins.com/gizmo/downloads/Gizmo-11.5.25.tar.bz2?attredirects=0&d=1)

would be cool to get me going. see also:
[http://forums.x-plane.org/index.php?showtopic=49913&st=20](http://forums.x-plane.org/index.php?showtopic=49913&st=20)
basically a shared lib. xcode project etc. are there.

---

### Post by schauerlich on 2011-08-29
It appears to rely on Carbon.framework, which is one of Apple's proprietary frameworks. Unless you know of an open source clone, you might be out of luck. Have you tried the windows version in Wine?

---

### Post by ahso4271 on 2011-08-30
No carbon is only needed for pathtranslation on OSX. Forget it on Linux.

---

### Post by nvteighen on 2011-08-30
> **ahso4271 said:**
> Gnustep seems very promising for future cross platform development, but for now I only do a x-plane plugin without gui. 


No. GNUStep is a mess that's lagging behind Cocoa... because the GNU ObjC compiler is stuck on ObjC 1.0. That's a major issue the FSF is struggling to solve, even by establishing GNUStep as a high-priority project. But without an ObjC 2.0 compiler, it's pretty hard to make GNUStep catch on 

Likewise, SideStep isn't doing any better.

---

### Post by ahso4271 on 2011-08-30
gcc/g++? even apple uses this awarded compiler...well evbd. does.

---

### Post by nvteighen on 2011-08-30
> **ahso4271 said:**
> gcc/g++? even apple uses this awarded compiler...well evbd. does.

IIRC, the current Apple Objective-C compiler is based on LLVM.

---

### Post by schauerlich on 2011-08-30
> **ahso4271 said:**
> gcc/g++? even apple uses this awarded compiler...well evbd. does.

Apple doesn't use the main GCC compiler. Theirs is based off of a fork of gcc 4.2, and has a lot of customizations that haven't been merged into GNU's GCC.

> **nvteighen said:**
> IIRC, the current Apple Objective-C compiler is based on LLVM.

Apple has 3 compilers available: gcc, llvm-gcc, and clang. gcc is the compiler Apple originally used, forked from 4.2 and customized for all of Apple's extensions to C/ObjC. llvm-gcc uses Apple's fork of gcc as a front end, with llvm doing the actual code generation. clang is a whole new front end based on llvm, with the goal of being more or less a drop in replacement for gcc. Currently, OS X defaults to llvm-gcc because clang's C++/ObjC++ support isn't quite production ready yet.

---

### Post by ahso4271 on 2011-08-30
IIRC Apple takes open source to create closed source incompatibilites? Why not give back like for ex. the frameworks crap that is complicating cross platform dev. :frown:
Yea that's why i only have osx86...

---

### Post by schauerlich on 2011-08-30
> **ahso4271 said:**
> IIRC Apple takes open source to create closed source incompatibilites? Why not give back like for ex. the frameworks crap that is complicating cross platform dev. :frown:
Yea that's why i only have osx86...

Frameworks are part of the Objective-C language, Apple had nothing to do with them. They're the equivalent of C libraries.

---

### Post by nvteighen on 2011-08-30
> **schauerlich said:**
> 
Apple has 3 compilers available: gcc, llvm-gcc, and clang. gcc is the compiler Apple originally used, forked from 4.2 and customized for all of Apple's extensions to C/ObjC. llvm-gcc uses Apple's fork of gcc as a front end, with llvm doing the actual code generation. clang is a whole new front end based on llvm, with the goal of being more or less a drop in replacement for gcc. Currently, OS X defaults to llvm-gcc because clang's C++/ObjC++ support isn't quite production ready yet.

Oh thanks.

> **ahso4271 said:**
> IIRC Apple takes open source to create closed source incompatibilites?

Not necessarily. The compiler might still be open source; the issue is that nobody seems to be porting those additions back to the GNU ObjC compiler (mainly because almost nobody uses it).

---

### Post by ahso4271 on 2011-08-31
> **schauerlich said:**
> Frameworks are part of the Objective-C language, Apple had nothing to do with them. They're the equivalent of C libraries.

I'll try to compile this c* on osx86 today. if it works the're different from standard Unix libs, as on Linux i get tons of missing headers and/or multiple declarations.

@nvteighen: surely a huge lot of very complicated work...so again why not give it back Apple, instead to pile up billions.

---

### Post by nvteighen on 2011-08-31
> **ahso4271 said:**
> 
@nvteighen: surely a huge lot of very complicated work...so again why not give it back Apple, instead to pile up billions.

Why would Apple give it back, if they can pile up billions? ;)

Yes, this world sucks.

---

### Post by JupiterV2 on 2011-08-31
[strikethrough]What about Clang/LLVM? Doesn't Apple fund/support it? Pretty sure it supports the latest standard of ObjectiveC but I seem to recall reading somewhere it has poor support of ObjectiveC++...[/strikethrough] - Missed the previous comment on this subject! Oops!

I just started noodling around with Clang last night. Didn't get much farther than compiling a trivial Hello World program due to time. Interestingly, I noticed the binary from Clang was smaller than the one built by GCC 4.6. I haven't had a chance to figure out why.

---

### Post by schauerlich on 2011-08-31
> **JupiterV2 said:**
> I just started noodling around with Clang last night. Didn't get much farther than compiling a trivial Hello World program due to time. Interestingly, I noticed the binary from Clang was smaller than the one built by GCC 4.6. I haven't had a chance to figure out why.

Here's [some benchmarks](http://www.phoronix.com/scan.php?page=article&item=gcc_llvm_clang&num=1) and [other information](http://clang.llvm.org/comparison.html) if you decide to continue your investigation.

---

### Post by JupiterV2 on 2011-08-31
Thanks Schauerlich. As a matter of fact, I had already viewed both pages already but I really appreciate the links. Faster compilation means far less to me than execution speed when it comes to my system libraries but for most user-level applications the speed of compilation may outweigh the loss of speed, depending on the overall effect. It will be interesting to see how Clang evolves as it continues to mature. I'm a little leery of Apple's involvement but as long as it remains with the BSD license I'd continue to use it.

I plan to do more testing with it. If anyone would like, I'd be happy to share my experience..

---

### Post by Simian Man on 2011-08-31
> **ahso4271 said:**
> Gnustep seems very promising for future cross platform development, but for now I only do a x-plane plugin without gui. 

Yeah, [this ]("http://www.gnustep.org/images/full-screenshot1.png")sure looks like the GUI of the future to me!

---

### Post by nvteighen on 2011-09-01
> **Simian Man said:**
> Yeah, [this ]("http://www.gnustep.org/images/full-screenshot1.png")sure looks like the GUI of the future to me!

Don't hit GNUStep that hard: it's unfair. The GNUStep desktop was created long ago as a reimplementation of the NeXTSTEP Desktop and they've done that quite well. OK, it's true that nobody uses NeXTSTEP anymore and you might think that it's nonsense to keep this project going on. The problem is that the NeXTSTEP Desktop and all its APIs are more or less the same thing, so you end up having to do it in order to get a usable OpenStep complying framework for Objective-C. True, this shows poor design by NeXT (i.e. Steve Jobs), but the guys at the FSF can't do anything about it.

A long-term solution would be to create an Objective-C Core Library that is completely decoupled from the OpenStep standard and messy madness. I remember participating in such an attempt, but we were so naïve thinking that we could actually produce such a thing :P

---

