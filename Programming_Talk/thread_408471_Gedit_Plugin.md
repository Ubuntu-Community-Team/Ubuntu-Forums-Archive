---
title: "Gedit Plugin"
date: 2007-04-13
forum: Programming Talk
---

### Post by almacen on 2007-04-13
Got advised to post here...so here it is....

Hi,
Quick question, I am trying to add a plugin to gedit so when I press say "F5" it complies my C++ code, I was thinking the command has to be something like this:

g++ %n -o main;

But this doesn't work, it says:

Running tool: g++
g++: %n: No such file or directory
g++: no input files

Any ideas?

Thanks a lot

Ali
Edit/Delete Message

---

### Post by rplantz on 2007-04-13
One solution is to create a Makefile for your program. (Not a bad idea, since most programs have more than one file.) Then Tools -> Build will run your Makefile. F8 is supposed to do this also. It does not on my system.

Edit: I just discovered that this bug has been reported ([http://bugzilla.gnome.org/show_bug.cgi?id=406176)](http://bugzilla.gnome.org/show_bug.cgi?id=406176)). Also, thank you, almacen, for your question; I did not know about the Build tool in gedit.

---

