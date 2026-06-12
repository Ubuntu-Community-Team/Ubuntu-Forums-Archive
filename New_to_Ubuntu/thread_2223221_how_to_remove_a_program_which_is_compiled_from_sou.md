---
title: "how to remove a program which is compiled from sources"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by -@23%^yu* on 2014-05-10
I have installed a programme called cgminer 3.7.2. Now I want to uninstall it, I have followed the instructions provided in the installation file. But when I type in the command I am able to execute the command. How to completely remove the programme?

---

### Post by oldos2er on 2014-05-10
We need to see all terminal output including the commands you run.

Normally you would go into the source folder (the same from which you ran "make install") and run ```
sudo make uninstall
``` but some programs may do this differently.

---

### Post by buzzingrobot on 2014-05-10
All but very simple applications consist of more than one file.  The usual directory for the specific executable file that runs is /usr/bin or, sometimes, /usr/local/bin.

The makefile used to build the app should specify where the various files are installed.

---

### Post by -@23%^yu* on 2014-05-24
I figured it out.
just 
> sudo make uninstall
and
> sudo make clean

---

