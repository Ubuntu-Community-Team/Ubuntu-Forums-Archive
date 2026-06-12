---
title: "[SOLVED] Problems with autotools optimizing code"
date: 2006-12-12
forum: Programming Talk
---

### Post by Keith Hedger on 2006-12-12
Hi guys Ive got a small problem with the autotools, I have got a project that is getting a bit big and so have started using autogen and the othe auto tools to handle the makefiles etc, no problem there but I cant get automake to stop !"£$%^%& puting the -g -O2 optimizations onto the end of the g++ command this makes debugging impossible! I just can't override the damned thing, Ive tried the various docs and man pages but no joy!
Please help otherwise Ive got to go bake to manually makeing my Makefiles](*,)

---

### Post by hod139 on 2006-12-12
Look in configure.ac for any CXXFLAGS containing the offending arguments.  If not in there, look in the Makefile.am files.

---

### Post by Keith Hedger on 2006-12-13
Thanks I added 'CXXFLAGS= "-ggdb -O0"' and problem solved!
:mad: 
But if these 'auto programs' are going to set flags by default they should at least  document what the hell they are doing!!!
:mad: 
Anyway thanks a lot:)

---

