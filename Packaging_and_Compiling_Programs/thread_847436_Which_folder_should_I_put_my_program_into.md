---
title: "Which folder should I put my program into?"
date: 2008-07-02
forum: Packaging and Compiling Programs
---

### Post by Johnsie on 2008-07-02
I've written a program for watching online TV stations. The main file is called stvlinux.sh

I'm looking at making a .deb installer for the program and wonder which folder I shoud make the stvlinux.shh file go into. I already know which one to put the icon into.

Anyone have any ideas?

It will work on almost any folder on the system but I want to try and be standard compliant. With windows it was c:/program files/appname but hey, it's not a windows app lol ;-)

---

### Post by pytheas22 on 2008-07-02
Most executables on Ubuntu go in /usr/bin.  You can put it lots of other places too, but /usr/bin would be the most common.

---

### Post by robertchahine on 2008-07-02
> **pytheas22 said:**
> Most executables on Ubuntu go in /usr/bin.  You can put it lots of other places too, but /usr/bin would be the most common.
+1.
i think usr/bin is a good folder to extract executable files to it.And for plugins folder to your applications /usr/lib is a good folder

---

