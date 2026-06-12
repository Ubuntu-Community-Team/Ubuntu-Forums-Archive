---
title: "QT Application binary"
date: 2011-02-27
forum: Programming Talk
---

### Post by sid.mallya on 2011-02-27
Hey I just learnt how to make an application in QT Creator using C++. The files I have created work on compiling in QT .. 

How do I make a binary of the files so it is executable without having to run QT ?

---

### Post by Vaphell on 2011-02-27
look in the project directory, binary should be right there. Usually there are 2 profiles of project (debug and release) and i think binaries should be located in related subfolders.

---

### Post by sid.mallya on 2011-02-27
****. I feel retarded now. =/

---

### Post by hakermania on 2011-02-27
In the directory with your source run:
```
qmake -project; qmake *.pro; qmake; make
```

---

