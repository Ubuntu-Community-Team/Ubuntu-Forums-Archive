---
title: "My first .deb :-) doesn't work :-("
date: 2009-10-16
forum: Packaging and Compiling Programs
---

### Post by Sandsound on 2009-10-16
Yay... I have just made my first .deb :-)

Problem is that it doesn't work i the package manager, but I can install it using dpkg :
```
sudo dpkg -i isometric_0.1-1.deb
```

Is there any way to debug a deb ? or perhaps someone can point out what I have done wrong.

edit : see post #6, new and almost working example here : [isometric_0.1-1_i386.deb]("http://www.sandgreen.dk//xt2/files/isometric_0.1-1_i386.deb")

---

### Post by baskar007 on 2009-10-16
> **Sandsound said:**
> Yay... I have just made my first .deb :-)

Problem is that it doesn't work i the package manager, but I can install it using dpkg :
```
sudo dpkg -i isometric_0.1-1.deb
```

Is there any way to debug a deb ? or perhaps someone can point out what I have done wrong.

[isometric_0.1-1.deb]("http://www.sandgreen.dk//xt2/files/isometric_0.1-1.deb")
Which package manager u r using?

---

### Post by Sandsound on 2009-10-16
> **baskar007 said:**
> Which package manager u r using?

I'm using GDebi (actually I just double-click it)

btw. I'm running Karmic

---

### Post by baskar007 on 2009-10-16
reinstall GDebi and try again?

how you packed the deb?
command or dhmake?

---

### Post by Sandsound on 2009-10-16
> **baskar007 said:**
> reinstall GDebi and try again?

how you packed the deb?
command or dhmake?

GDebi is NOT the problem, it works fine with all other .deb files.
The problem is my self-generated .deb file

I used ```
dpkg-deb --build isometric_0.1-1
```

---

### Post by Sandsound on 2009-10-17
I found this how-to : [http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb]("http://showmedo.com/videotutorials/video?name=linuxJensMakingDeb")

Now my .deb actually works with GDebi, but it is only usable as root ?
The .deb installed it in /usr/share/isometric/

[isometric_0.1-1_i386.deb]("http://www.sandgreen.dk//xt2/files/isometric_0.1-1_i386.deb")

edit : I was using : 
```
sudo dpkg-buildpackage
```
Tried again with : 
```
dpkg-buildpackage -rfakeroot
```
And now it works

---

