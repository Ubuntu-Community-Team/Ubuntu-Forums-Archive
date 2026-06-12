---
title: "distributing Python GUI Apps to computers without python"
date: 2007-02-12
forum: Programming Talk
---

### Post by kthakore on 2007-02-12
I have made a PyQt4 GUI and I want to distribute them to other linux and windows computer without having them to install all the various modules I used and python. 

I know for linux there is freeze.py, but I can't get it to work with python2.4

also I have had some success with py2exe for windows machines, but I want to be able to make the exe on my ubuntu computer. 

These are the modules I use

```

sys
PyQt4
serial

```

---

### Post by ssam on 2007-02-12
to distribute to ubuntu/debian/linspire computers a .deb is best. it contains a list of dependencies, which the computer can automatically install. also it can be installed by double clicking.

---

### Post by kthakore on 2007-02-12
how do I make .deb files for python?

also how would I make windows executable?

---

### Post by siman on 2007-02-12
for a windows exe, the best I found is py2exe - afaik you need to "compile" the exe on windows, though

---

### Post by disturbedite on 2007-02-12
> **kthakore said:**
> how do I make .deb files for python?

bump

i grabbed the source for pyscrabble (since i can't find a deb package) and i don't have any python experience so i don't know what to do with it.  i'd like to make a deb package of it.

---

### Post by WW on 2007-02-12
EPM ([http://www.easysw.com/epm/](http://www.easysw.com/epm/)) is a handy tool for creating .deb files. It can also create .rpm files, and other package formats.

---

