---
title: "qt header file missing message while compiling qdvdauthor"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mmasroorali on 2008-06-07
While trying to compile qdvdauthor-1.2.0 in Ubuntu hardy heron(I was trying to get rid of bugs in the default included version 1.1.0), I get messages in the following line, 

main.cpp:17:26: error: qapplication.h: No such file or directory
main.cpp:18:24: error: qtextcodec.h: No such file or directory
main.cpp:19:23: error: qfileinfo.h: No such file or directory
main.cpp:20:18: error: qdir.h: No such file or directory
..............
global.h:16:21: error: qstring.h: No such file or directory
global.h:17:24: error: qeventloop.h: No such file or directory
global.h:18:24: error: qvaluelist.h: No such file or directory

It appears that some qt libraries are missing. But I can not locate which ones. I have already installed g++ and qt-devel without any avail.

Any hints will be appreciated.

---

### Post by Oldsoldier2003 on 2008-06-07
> **mmasroorali said:**
> While trying to compile qdvdauthor-1.2.0 in Ubuntu hardy heron(I was trying to get rid of bugs in the default included version 1.1.0), I get messages in the following line, 

main.cpp:17:26: error: qapplication.h: No such file or directory
main.cpp:18:24: error: qtextcodec.h: No such file or directory
main.cpp:19:23: error: qfileinfo.h: No such file or directory
main.cpp:20:18: error: qdir.h: No such file or directory
..............
global.h:16:21: error: qstring.h: No such file or directory
global.h:17:24: error: qeventloop.h: No such file or directory
global.h:18:24: error: qvaluelist.h: No such file or directory

It appears that some qt libraries are missing. But I can not locate which ones. I have already installed g++ and qt-devel without any avail.

Any hints will be appreciated.

```
sudo apt-get build-dep qdvdauthor
```Should sort you out 
Also make sure you have build-essential installed

---

