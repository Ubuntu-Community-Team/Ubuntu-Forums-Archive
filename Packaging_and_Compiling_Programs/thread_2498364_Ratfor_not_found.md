---
title: "Ratfor not found???"
date: 2024-06-10
forum: Packaging and Compiling Programs
---

### Post by eldarnoe on 2024-06-10
Hi folks,

I'm having the strangest experienece.  I am attempting to use make to make a file.  This makefile compiles a bunch of stuff to generate an executable.  In the past, I had no problem using it to generate my compilation.  However, last week I tried to run make again and got the following error (The ">" at the start of a line in this thread precedes a command I typed, for clarity):


>sudo make install |& sudo tee make.1.cube.out.txt
f77    -c -o ../specpr/src.specpr/common/spblockdata.o ../specpr/src.specpr/common/spblockdata.r
f77: error: ../specpr/src.specpr/common/spblockdata.r: Ratfor compiler not installed on this system
make: *** [<builtin>: ../specpr/src.specpr/common/spblockdata.o] Error 1

If I just type ratfor from my command prompt, I get:

>ratfor
C Output from Public domain Ratfor, version 1.04


so it does seem to exist.  
I figured maybe I should try reinstalling ratfor using:

>sudo apt-get -y install gfortran ratfor gfortran-doc

Reading package lists... Done
Building dependency tree
Reading state information... Done
gfortran is already the newest version (4:9.3.0-1ubuntu2).
gfortran-doc is already the newest version (4:9.3.0-1ubuntu2).
ratfor is already the newest version (1.04-1).
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.


No issues.  I am at a complete loss.  Anybody have any idea how I can start troubleshooting this?

Thanks

---

### Post by TheFu on 2024-06-10
I haven't used FORTRAN since the 1980s and never on Linux.  I suspect you broke the makefile by replacing tabs with spaces or sometime like that.  Editors often have settings that change between tabs and space or spaces and tabs.  Makefiles are tab-sensitive.

You'll need to post the raw Makefile (unmolested) to get help.  You'll also need to use forum code tags whenever posting anything from a terminal, if you expect to get useful help.

---

### Post by eldarnoe on 2024-06-11
> **TheFu said:**
> I haven't used FORTRAN since the 1980s and never on Linux.  I suspect you broke the makefile by replacing tabs with spaces or sometime like that.  Editors often have settings that change between tabs and space or spaces and tabs.  Makefiles are tab-sensitive.

You'll need to post the raw Makefile (unmolested) to get help.  You'll also need to use forum code tags whenever posting anything from a terminal, if you expect to get useful help.

Hi, thanks for your feedback. I'm brand new at forums and I'm still on the learning curve, so I appreciate the pointers.  When you say post the raw makefile, do you mean cut/paste the contents?  Or is there a way to upload it?

---

