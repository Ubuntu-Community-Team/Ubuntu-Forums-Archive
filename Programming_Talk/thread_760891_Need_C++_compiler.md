---
title: "Need C++ compiler"
date: 2008-04-20
forum: Programming Talk
---

### Post by nick22891 on 2008-04-20
Need a C++ compiler for my ubuntu, preferably a dev C++ kind of IDE but any compiler will do. ANyone know of any and how to get it?

---

### Post by Oldsoldier2003 on 2008-04-20
> **nick22891 said:**
> Need a C++ compiler for my ubuntu, preferably a dev C++ kind of IDE but any compiler will do. ANyone know of any and how to get it?

```
sudo apt-get install build-essential
``` will install the compiler and support files. if you want an IDE there are many other opitions such as eclipse.

---

### Post by LaRoza on 2008-04-20
See the sticky in the programming talk.

---

### Post by Joeb454 on 2008-04-20
If you want a **compiler** then Open up a terminal and type ```
man g++
``` that's the GNU C++ Compiler :)

If you want an **IDE** then look into Ecplise or something, personally I use Kate for my coding, it supports Syntax highlighting for all languages I code in :)

---

### Post by martrn on 2008-04-20
If you need an IDE install then you can

```
sudo apt-get install anjuta
sudo apt-get install kdevelop

```

And they are the top IDE's if you are developing QT/GTK  or X11 windows applications.  Many people compile applications from the command line, if you do not need an IDE you can install g++ and build-essentials without an IDE.  Some people even use a notrpad like kate to write widges and avoid IDE's alltogether but I personall find kevelop is good.

I haven't managed to get Glade/Anjuta  to work with the GTK widgets yet.  You would need to also install a few dependcies.  IIf you know the answer to that please let me gnow.  I use kdevelop / QT widges anyway.

---

### Post by Sinkingships7 on 2008-04-20
I prefer Geany. After you install build-essential, type:
```
sudo apt-get install geany
```
It's as easy as F8 to compile, F9 to link, and F5 to run.

---

### Post by jespdj on 2008-04-21
If you want to develop software for the GNOME desktop, then install the package gnome-devel:
```
sudo apt-get install gnome-devel
```
This will get you a set of tools, including the Anjuta IDE, and developer documentation.

+1 for Geany, it's a really nice light weight editor / IDE.

---

