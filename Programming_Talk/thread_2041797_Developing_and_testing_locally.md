---
title: "Developing and testing locally"
date: 2012-08-13
forum: Programming Talk
---

### Post by davidlinn on 2012-08-13
I'm thinking of contributing to an open source project and was wondering about how to test a developement version of the project. I'm new to ubuntu. The instructions for installation are ./configure, make and make install. Do I have to repeat it every time I make a change ? Also, make install would mess with the installed stable version of the software. How do I keep it local ?

---

### Post by trent.josephsen on 2012-08-13
Technically there's no guarantee, but usually the following will apply:

- If all you do is edit the source code, you *probably* don't have to re-run ./configure before running make;

- It's *probably* possible to run the compiled application from the build folder without running `make install`. You may have to fiddle with the environment so the binary knows where to find the application files that would otherwise be saved in /usr somewhere. Poorly implemented software may not be able to handle this.

Your best bet is probably to look for documentation on the project (be sure to read the README file thoroughly). If that doesn't give you any clues, write the project's mailing list or post on a developer's forum, and ask how the official devs do testing.

---

### Post by ofnuts on 2012-08-13
> **davidlinn said:**
> I'm thinking of contributing to an open source project and was wondering about how to test a developement version of the project. I'm new to ubuntu. The instructions for installation are ./configure, make and make install. Do I have to repeat it every time I make a change ? Also, make install would mess with the installed stable version of the software. How do I keep it local ?
./configure normally lets you specify a "prefix" which is really where the program will be installed (usually in /opt, or some user directory). As said above you don't need to run it every time (but you may run it several times at the beginning while you work out the dependencies).

Unless you are a programming genius and do everything right the first time, you will use "make" a lot more often than "make install".  But nothing prevents you from writing a short script that launches "make" and then "make install" if "make" was successful.

---

