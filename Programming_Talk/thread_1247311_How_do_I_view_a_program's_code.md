---
title: "How do I view a program's code?"
date: 2009-08-22
forum: Programming Talk
---

### Post by BardSeed on 2009-08-22
Sorry if this has been asked before; I did search. I'm starting to learn programming with python. I feel that I need to be able to see how other people use their programming tools to give me some ideas, but I've realised that I don't know how to find the code of any installed programs.
I'd be grateful for an answer, thanks.

---

### Post by zarthon on 2009-08-22
This may get you started with some code to look at but it's not all particularly good for examples:
The following commands give almost ridiculously large results to be very useful but show you where most of the python code is on your system.

```
ls /usr/lib/python*/site-packages/*/*py
```

Their are better examples in /uer/share/doc/

```

ls /usr/share/doc/*/*/*.py
and also
ls /usr/share/doc/*/*.py

```

---

### Post by zarthon on 2009-08-22
Better command after some experimenting ! 

```
ls /usr/share/doc/*/examples -d | grep python
```

Cheers !

---

### Post by tom66 on 2009-08-22
try "locate .py": on my system, 15326 results.

---

### Post by geirha on 2009-08-23
While you can look for python files in the system files, it's better to just download the corresponding source package for the package you want to look at. You do that with apt-get source. The gnome-games package contains some small games, of which at least the sudoku and chess is written in python, so try
```
apt-get source gnome-games
```
You'll also be able to look at how the files are organized, and how they are built and installed.

---

### Post by exutable on 2009-08-23
You can also look for program sources on sites like [http://sourceforge.net]("http://sourceforge.net"), [http://freshmeat.net]("http://freshmeat.net") and [http://launchpad.net]("http://launchpad.net").  Using SVN, CVS and other tools you can download the source for most open source projects.

I personally recommend using Eclipse with the subclipse plugin. You can then use CVS and SVN in one IDE.

Dane

---

