---
title: "Need help compiling when headers are not available in repos"
date: 2010-02-22
forum: Packaging and Compiling Programs
---

### Post by ridetheteapot on 2010-02-22
Hey I am having a little trouble compiling a plugin for a program that i compiled a while back. The -dev package available in the repos is an earlier version than what i am running.

Specifically i am trying to compile the dynamic playlist plugin for gmpc with cmake; and i cannot use the headers in the repo because libmpd and gmpc are compiled svn snapshots.
Maybe i am having a brain fart because i have numerous other plugins compiled -- but i dont know the neatest way to get the headers for my version included for make.

When i want to use custom libraries for a binary i can export LD_LIBRARY_PATH=/blah:$LD_LIBRARY_PATH - can i do something like that?

Would it be more appropriate to make my own -dev packages as i need them? if so can someone point me in the right direction - never tried to make a header package).

TIA

---

### Post by Bachstelze on 2010-02-23
Normally when you compile a library from source and install it with [font=monospace]make install[/font], the relevant headers are installed as well. Or do you mean you did *not* use [font=monospace]make install[/font] on it?

---

### Post by ridetheteapot on 2010-02-23
no can not get it to build with make -

or do you mean when i previously built the snapshot of gmpc - i installed it with checkinstall

---

