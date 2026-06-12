---
title: "Good Linux Tutorials"
date: 2010-05-26
forum: Programming Talk
---

### Post by d00derino on 2010-05-26
I'm a computer science major who's embarrassed to say that I have little experience working with Bash, and the Operating System as a whole. I've taken Operating Systems. I've created simulations of disk head reading algorithms, and threading, and processes, but the class never applied any of it, like I thought it would.

Searching Google for Linux programming tutorials is like getting a square peg into a round hole. I get nothing. I've gotten TuxRadar, but even then, that site's tutorials are so outdated that I can barely use the tutorials because the packages used are outdated!

Anybody have any good links?

---

### Post by BoneKracker on 2010-05-26
BASH:

[http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

You can do a lot more in the shell than most people realize.  I have written an entire single-packet authentication daemon in a few hundred lines of BASH (and it's been running on my firewall for several years).

As to programming in general on Linux, I suggest messing around with C for a while first, since a lot of the stuff you'll want to reuse or interface with is done in C (the kernel, libraries, utilities, etc.).  Before diving into an IDE (I would recommend Eclipse, which handles many languages), it's a good idea to first minimize distractions and focus on learning the underlying GNU/Linux tools, by working in a command-line environment.

Start by familiarizing yourself with vim, and use that to code some basic programs.  Then learn how to use the GNU build system (there are other alternatives, but that one is elemental to Linux); write a simple make file for your simple program, and build it.  Debug it using gdb. Work through a couple tutorials.  Maybe try some simple projects of your own.
[http://www.google.com/search?q=C+programming+for+linux](http://www.google.com/search?q=C+programming+for+linux)

Then, you might like to focus on Python, C++ or something else.  You might choose to migrate to using an IDE and/or an alternative build system.  As a Computer Science major, you might enjoy fooling with Haskell or exploring Sun's collection of java-related open-source endeavors.  You might want to immerse yourself in networking, databases or middleware.  You might want to get involved in a project or a linux distribution as a tester, maintainer, or developer.

---

### Post by d00derino on 2010-06-06
Thanks. I've been meaning to thank you for a while now, but I've been really busy lately. 

Thanks again, I'll be off looking for Bash coding projects once I finish my post-session classes in a week!

---

