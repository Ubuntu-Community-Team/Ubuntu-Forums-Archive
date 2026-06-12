---
title: "Compiling for Windows"
date: 2011-01-06
forum: Packaging and Compiling Programs
---

### Post by Cobalt McDennis on 2011-01-06
Hey,
 
So this is a touchy subject i'm sure....but I am trying to compile an application called iperf([http://sourceforge.net/projects/iperf/](http://sourceforge.net/projects/iperf/)) in Ubuntu to create a windows executable.
 
There are instruction sets in the c and cpp files for running under windows, the program appears to be able to run properly under windows, but I am having a hard time trying to actually figure out how to do this.
 
I have tried using winemaker, and using the ./configure switches --build and --host etc..using the mingw32 packages from apt.
 
I can create an executable in cygwin no problem but of course it needs a cygwin dll to run properly which isn't an option.
 
I am aware that there is a version already compiled into an executable however it is a very old version that appears to be causing some problems on our windows servers, and I wanted to find out if compiling the new versions would fix the problems I am seeing.
 
There are a few other compiled executables running more recent versions of iperf but none of them work....which I am hoping is probably due to how they were compiled and not inherent in the fact that compiling in Linux for windows executables doesnt work. :)
 
Any thoughts? Ideas? Hints? Tips?
 
Thanks so much!

---

### Post by jacky.alcine on 2011-01-12
Well, lol, sounds like an interesting and weird problem. I'll look for solutions in my spare time, but the most I can tell you is to run a copy of Windows in a VM and try compiling it there. 

Have you tried looking for the missing cygwin .dll and executing it under Wine?

---

