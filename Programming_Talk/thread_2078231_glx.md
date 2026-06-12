---
title: "glx"
date: 2012-10-30
forum: Programming Talk
---

### Post by thedardanius on 2012-10-30
hey.

I downloaded sude apt-get install build-essential
but I didnt got glx or xlib or gl libs to develop gl apps. How can I get these?
Im new to linux development ;p

---

### Post by spjackson on 2012-10-30
For Xlib, you need to install libx11-dev. (See a response to your earlier post where *-dev packages were mentioned.)

What might be a good idea is to see which packages are needed to build say gtk, then you can pick which ones of these you think you need.
```

sudo apt-get build-dep libgtk-3-0

```
You can cancel the install before it starts, so you don't need to pull everything in that's needed for gtk, but you will get a list that you can pick and choose from.

---

### Post by thedardanius on 2012-10-30
ok and how do I get the opengl dev?

---

### Post by spjackson on 2012-10-30
In my previous example, I picked something that uses X and got its build dependencies. This time I'll pick something that uses opengl and find its dependencies.
```

apt-get build-dep freeglut3

```
I know you don't want glut because that's too high level for you, but by looking at the dependencies you should be able to work out what you need.

If you know the name of a header you need, and you have apt-file installed, then you can search to find what package installs it, e.g.
```

apt-file find stdio.h

```

---

### Post by thedardanius on 2012-10-30
ok, so if I want opengl I should type:
sudo apt-get build-dep opengl32
 
right?
 
and for glX:
sudo apt-get build-dep glx11?

---

### Post by spjackson on 2012-10-30
If there were packages named opengl32 and glx11 then maybe you could do that. But since these packages do not exist, you will get:
```

$ sudo apt-get build-dep opengl32
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to find a source package for opengl32

```
If, however, you do:
```

sudo apt-get build-dep freeglut3

```
then the exact results depend on what you already have installed, but it may list for example libgl1-mesa-dev libglu1-mesa-dev.

I don't know what opengl32 is apart from a Windows dll.

---

### Post by thedardanius on 2012-10-31
sry, im still with my head in windows. How is opengl dev called in linux? gl?

---

