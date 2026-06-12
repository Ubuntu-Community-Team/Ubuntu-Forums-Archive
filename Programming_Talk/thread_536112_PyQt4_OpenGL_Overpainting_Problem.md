---
title: "PyQt4 OpenGL Overpainting Problem"
date: 2007-08-27
forum: Programming Talk
---

### Post by Triscuit713 on 2007-08-27
I am using Feisty and the repo version of PyQt4 to write a program using OpenGL.

I have an Nvidia GeForce3 using the drivers provided in the respository.

The file usr/share/doc/python-qt4-doc/examples/opengl/overpainting.py doesn't run. I get errors saying something about a pointer that shouldn't be changed while running (I'm not in front of my computer to verify the exact error). Does anyone else get this error? Has anyone else figured a way to rid themselves of it?

---

### Post by Triscuit713 on 2007-08-27
If anyone could report to me the results of 

```
python usr/share/doc/python-qt4-doc/examples/opengl/overpainting.py 
```

I'd be most appreciative.

You need to do


```
apt-get install python-opengl python-qt4-dev 
```


to get the appropriate deps.

---

