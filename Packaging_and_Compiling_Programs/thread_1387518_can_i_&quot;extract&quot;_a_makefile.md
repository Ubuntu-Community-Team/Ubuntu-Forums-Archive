---
title: "can i &quot;extract&quot; a makefile"
date: 2010-01-22
forum: Packaging and Compiling Programs
---

### Post by pavel989 on 2010-01-22
hello everyone.
I wanted to make a few modifications to the gnome log file viewer.
after searching for a while for the sourcecode, i had found it.

i imported the code files into codelite, and when i went to compile, i had many many include and define errors. i started to go through and fix them when i noticed a pattern. so i went to the makefiles and found that they have all the corrections.

however, im trying to compile with gcc. is there a way to extract the information i need from a makefile? 

or can i include it in a gcc command?

---

### Post by SevenMachines on 2010-01-22
is there some reason your not just using the supplied Makefile to compile it with gcc? you could in theory go through it and tediously pick out the options you need to add to a gcc command line but why do that when you can just run make and have it do it for you

---

### Post by pavel989 on 2010-01-22
for debugging

---

### Post by SevenMachines on 2010-01-22
Usually the Makefile will use CFLAGS, which you can add any gcc options to like -g for debugging. Or even pass them from the command line, 
$ CFLAGS=-g -Wall make

---

### Post by pavel989 on 2010-01-23
i think the problem is that the logfileviewer is part of gnome-utils and u have to compile the entire package.

---

