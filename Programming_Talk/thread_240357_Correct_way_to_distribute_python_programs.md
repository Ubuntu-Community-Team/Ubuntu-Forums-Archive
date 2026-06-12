---
title: "Correct way to distribute python programs?"
date: 2006-08-20
forum: Programming Talk
---

### Post by npodges on 2006-08-20
I've started programming in python recently, but I'm pretty new at it.

What is the correct way to distribute a file? Is there a way to compile?

---

### Post by baldy1324 on 2006-08-20
since you are just starting in python you are probably just working with single-source code projects. all u have to do is get the other person the file and type```
python filename
```
you dont have to compile things in python b/c it is an interpreted language and interpreters do both at the same time.
hope that helped

---

### Post by scxtt on 2006-08-20
make sure the file is executable and that you have the line **#!/usr/bin/python** as the 1st line and all you need to do is type **./python_program.py** into a terminal and it will execute ...

---

### Post by npodges on 2006-08-20
Okay, but let's assume I weren't a new python programmer, and I was making more complex programs, and I wanted to distribute them as installable packages. Is there a way to compile?

For example, at ubuntu.com, they say that they prefer all code to be written in python. How do they compile it before release?

Thanks,
nick

---

### Post by Daverz on 2006-08-20
Most python projects use distutils so users just have to unarchive the tarball, cd into the directory, and type

sudo python setup.py install

You might take a look at some non-trivial python programs and copy from their setup.py.

You might want to go farther and produce a .deb or .rpm of your project.

For windows distribution, you can use py2exe and the inno setup installer.  I don't think I've seen anything that does that for unix, though.

---

### Post by Note360 on 2006-08-21
Ya you will need a setup.py . Actually go to the scribes site [http://scribes.sourceforge.net/download.html](http://scribes.sourceforge.net/download.html) and download the source code. Inside their is a setup.py . Also you can dl the prototype versions and copy off of the configure and MAKEFILE. To get a ./configure and make install installation

---

### Post by Daverz on 2006-08-21
> **Daverz said:**
> For windows distribution, you can use py2exe and the inno setup installer.  I don't think I've seen anything that does that for unix, though.

Correction: that didn't parse right.  What I meant to say is that I've never seen a project that distributed a "frozen" distribution of their code, but Python does come with a freeze script, and there is cx_freeze for unix.  It's probably more for distributing to clients who can't install Python for various reasons rather than for distributing to typical Linux desktop users.

---

