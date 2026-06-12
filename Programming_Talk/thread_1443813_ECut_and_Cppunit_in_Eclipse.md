---
title: "ECut and Cppunit in Eclipse"
date: 2010-03-31
forum: Programming Talk
---

### Post by tetebueno on 2010-03-31
Hi, I've been trying to set up a project in Eclipse to run with CppUnit tests, but no luck so far, here are the steps I've followed:

1. Get libcppunit with:
```
sudo apt-get install libcppunit-1.12-1 libcppunit-dev
```

2. Get the Ecut plugin from [http://sourceforge.net/projects/ecut/](http://sourceforge.net/projects/ecut/) and installed it in Eclipse with the software installer in the Help menu.

3. Configured the connector in Eclipse in Window -> Preferences -> C/C++/ECUT -> Configure (I just added "Library location: /usr/lib/libcppunit.a" and "Include location: /usr/include/cppunit" and that was it).

4. Right click in the project I wish to use with ECUT -> Apply Connector. And setup a folder in the project for the test's source files (I also had to filter the file containing the project's main() in the build folders for the new ECUTTest build configuration).

The problem, when I try to make a new ECUT file (with right click on a folder: New -> Other -> ECUT Test Case), no parent class can be found when browsing for a super class. I think this has to do with the fact that I can't get autocompletion when writting a CppUnit class in a file while developing.
Also, If I copy and paste a source code of a complete test in a file and try to run it as an ECUT test, the Eclipse's ECUT view.
So, it seems something must be misconfigured somewhere because it's just like no CppUnit code was there. Anybody? Thanks.

ps: maybe this is a thread for Eclipse's forum, but since this worked in an Eclipse under Wilson and I've solved lots of issues in Ubuntu looking into this forum, I'll give it a shot.

---

### Post by lermit on 2010-04-25
Hi tetebueno,

you say 
> no parent class can be found when browsing for a super class.
Is your source code in a "simple" folder instead of a source folder ? :P

Have fun,

Lermit

---

### Post by tetebueno on 2010-12-27
Man, it's been a while since then... I'll be joining a C++ project again soon, I'll be sure to check that to answer here again.
Thanks.

---

