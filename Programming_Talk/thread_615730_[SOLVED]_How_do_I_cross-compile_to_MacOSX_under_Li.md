---
title: "[SOLVED] How do I cross-compile to MacOSX under Linux?"
date: 2007-11-17
forum: Programming Talk
---

### Post by volanin on 2007-11-17
Hello,

I am doing a game-project under Linux (my favorite development platform),
and I already got it compiling and running in Linux (with both gcc and intel-icc),
and Windows, by cross-compiling with mingw32 under Linux.

The great thing about it is that I don't even have Windows installed in my notebook.
All the Windows programming was done under Linux itself with the cross-compiler.
Only the testing was performed native under Win32 in my desktop computer.

I'd also like to port this to MacOSX, effectively enabling it to run under the three
major OSes out there, but I could find no cross-compiler for the INTEL-BASED
MacOSX system out there, so that I can develop to it under Linux, just as I
do with Windows right now.

Can someone point me in the right direction?
Thank you a lot!
:)

---

### Post by ThinkBuntu on 2007-11-17
You could forward the source to a Mac user. You need XCode to compile for a Mac, as far as I know. 3.0 is for Leopard, 2.5 is for earlier development.

---

### Post by dwhitney67 on 2007-11-17
Porting code to compile on a different platform is one thing.   Compiling it on one platform to work on another (which is cross-compiling), is different.

GCC should be able to allow you to cross-compile.  I believe that the Mac uses a PPC (power PC) architecture.  If you are planning to use shared libraries, then you had better cross-compile those too (on your local system).

The easiest alternative is to provide source code for the game, and let the end-user compile the application.

If you are looking to build yourself a cross-compiler, you can try referencing Cross-Compiler HowTo's on the web.  A couple that I have tried include Dan Kegel's ([http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/)) and Cross-Compiled Linux From Scratch ([http://www.linuxfromscratch.org/clfs/view/1.0.0](http://www.linuxfromscratch.org/clfs/view/1.0.0)).  For the latter, you do not need to build the entire OS... just the cross compiler.

I've written C++ code before under Solaris and compiled it for the Power-PC.  I used the GCC compiler, so I know it is possible.

---

### Post by ThinkBuntu on 2007-11-17
> **dwhitney67 said:**
> Porting code to compile on a different platform is one thing.   Compiling it on one platform to work on another (which is cross-compiling), is different.

GCC should be able to allow you to cross-compile.  I believe that the Mac uses a PPC (power PC) architecture.  If you are planning to use shared libraries, then you had better cross-compile those too (on your local system).

The easiest alternative is to provide source code for the game, and let the end-user compile the application.

If you are looking to build yourself a cross-compiler, you can try referencing Cross-Compiler HowTo's on the web.  A couple that I have tried include Dan Kegel's ([http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/)) and Cross-Compiled Linux From Scratch ([http://www.linuxfromscratch.org/clfs/view/1.0.0](http://www.linuxfromscratch.org/clfs/view/1.0.0)).  For the latter, you do not need to build the entire OS... just the cross compiler.

I've written C++ code before under Solaris and compiled it for the Power-PC.  I used the GCC compiler, so I know it is possible.
Mac uses an Intel architecture very often, in fact it uses a "Universal" architecture preferably until the PPCs die off.

Also, to havea  true "Carbon" or even "Cocoa" or "Aqua" application, you'll need to go into XCode on a Mac. There's more to it than cross-compiling.

---

### Post by Auria on 2007-11-17
On mac OS X we use a special GCC version modified by Apple - i am unsure whether regular GCC is able to do it.

Anyway OS X uses many concepts rather different from linux, like frameworks and app bundles. getting cross-compile to work would be rather difficult i believe.

---

### Post by volanin on 2007-11-18
Yes, indeed you all are right.
It's not so trivial as MingW for Win32. I really got to install XCode.
Well, time to shrink my linux partition to free some extra space to MacOSX!
Thank you everybody!
:)

---

### Post by horvatj on 2007-11-19
Hi there,

I have the same problem, but

THE OTHER WAY AROUND!

I want to develop for Linux (x86) under MacOSX (Intel, 10.5).

May someone give me some hints?

Thanks in advance...

Johann

---

