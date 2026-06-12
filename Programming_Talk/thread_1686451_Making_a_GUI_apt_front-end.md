---
title: "Making a GUI apt front-end"
date: 2011-02-12
forum: Programming Talk
---

### Post by wrix on 2011-02-12
Hi, I was wondering to write a GUI front-end to Apt, like Synaptic, just to gain knowledge. I have some working knowledge of Tcl, Bash and bit of C. But I am unable to find any resources for my reference, please help.

---

### Post by MadCow108 on 2011-02-12
bash and C are not very well suited for gui programming. Don't know how good tcl is but I guess you should probably also learn a language which supports object orientation directly (e.g. python, C++, Vala, ...).

here are python bindings to apt
[http://apt.alioth.debian.org/python-apt-doc/](http://apt.alioth.debian.org/python-apt-doc/)
(includes python to c++ bindings)

---

### Post by llanitedave on 2011-02-12
I don't have any direct experience with tcl, but from what I've read it should work.  It is integrated with tk, which has a GUI development capability built-in.

And Python also uses tcl/tk bindings to produce it's default GUI package, TKinter.

Python should be able to produce a Synaptic-like application relatively easily.

---

### Post by scott_tiger on 2011-02-12
Java will be prefered to create GUI apps

---

### Post by cariboo on 2011-02-12
Have a look at Quickly, it is a combination of perl and glade, quickly is in the repositories.

---

### Post by nvteighen on 2011-02-12
You have two problems here:

1) You need a language that can interact with libapt.
2) And *then* you need a language that has a GUI library.

Python can be a good choice here and, IMO, the best choice. But no matter if best or not, it's definitely a good one :) It has libapt bindings and writing GUIs in it is quite easier than in other environments (either using a GUI designer or by hand). Also, being a dynamic language saves you from a lot of hassle that you have to do in other languages... at the cost of performance, as usual, but that can be ignored in this case.

Perl is also a good choice, but it's a language rather hard to master. I'd also try it, because it's far more flexible than it seems at first sight. Also has bindings to libapt and to the usual GUI toolkits.

Tcl/Tk has the advantage that it's a GUI-oriented language. But I don't know if it has libapt bindings and, honestly, I don't know the language either, so I can't give any further advice.

Now, another problem is what GUI toolkit you want. GTK+ and Qt are the most popular and most powerful out there, but both are fairly complex APIs. IMO, the only thing to take in account here is that there's no way to use Qt with C... something that seems irrelevant to your case. In the end, the GTK+ vs. Qt choice is usually resolved by taste or by platform-targeting (GNOME vs. KDE, respectively, though you can execute GTK+ or Qt programs in any X11 desktop environment).

---

### Post by juancarlospaco on 2011-02-12
Python.

You don't need libapt bindings ON the Gui Toolkit, thats backend job.

Dont worry Python got bindings to APT.

---

