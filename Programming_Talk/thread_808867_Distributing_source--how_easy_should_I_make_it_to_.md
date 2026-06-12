---
title: "Distributing source--how easy should I make it to compile?"
date: 2008-05-26
forum: Programming Talk
---

### Post by srhlefty on 2008-05-26
I've noticed that the vast majority of source packages use the ./configure && make method of compiling programs.  I've just recently begun distributing a non-trivial (6 binaries & 4 internal libs) game that I wrote using Eclipse as my IDE, and it sure would be nice to conform to the "standard" way of doing things.  

The way my source tree is set up, it can be imported into Eclipse as a workspace and then everything gets built automatically.  My question is then, is it good enough to just give people the source tree (with the appropriate .cdtproject etc files), and tell them how to import it into Eclipse?  Or should I go through the extra effort to try and generate a more standard package?  Or maybe a third option I haven't thought of?

---

### Post by amingv on 2008-05-26
I'd suggest to stick to the regular methods (./configure && make or autoconf), myself I wouldn't like to have to install another IDE just to use (or try) a program.
That also would make it easier to make a .deb in the future, if you're into serious stuff; of course, I'm not talking from experience here, just vague experiments.

---

### Post by WW on 2008-05-26
> **srhlefty said:**
> 
My question is then, is it good enough to just give people the source tree (with the appropriate .cdtproject etc files), and tell them how to import it into Eclipse?  Or should I go through the extra effort to try and generate a more standard package?

I think you answered your own question:
> **srhlefty said:**
> 
and it sure would be nice to conform to the "standard" way of doing things.

Requiring that Eclipse be installed to compile your program is not a "standard" way of doing things.  autoconf and its related tools are a pain, but setting up a configure script is probably the most widely used system for distributing source code.
> **srhlefty said:**
> 
Or maybe a third option I haven't thought of?

Another option is [cmake](http://www.cmake.org/); less widely used is [scons](http://www.scons.org/).

---

### Post by JupiterV2 on 2008-05-27
If you don't want to go the extra mile to create a .deb or .rpm package, then standard practice is to use the GNU autotools (automake, autoconf, autoheader, aclocal and libtools(am I missing one?)). These tools will allow you to create a "standard" deployment platform for compiling and installing libraries and binaries via the typical: ./configure && make && make install

Honestly, once you take the time and effort to learn them they're almost easier than creating your own custom Makefile, especially when it comes to portability.

---

### Post by srhlefty on 2008-05-28
Thank you all for the advice.  I've decided to begin the descent into "autohell"! :)

---

