---
title: "gnome-main-menu"
date: 2007-11-22
forum: Packaging and Compiling Programs
---

### Post by Venko on 2007-11-22
Hey,

I took a look at gnome-main-menu (SLAB) yesterday and figured that I could make use of it with some customisation. So I downloaded the source and the dependencies:

```
sudo apt-get source gnome-main-menu
sudo apt-get build-dep gnome-main-menu
```

I then proceeded to modify it to my needs. Afterwards I compiled it:

```
./configure
make
sudo make install
```

However the applet does not show up in "Add to Panel..."

Naturally I assumed I had broken the source workings somehow so I uninstalled the program, downloaded a clean version of the source again and compiled this without any modification. The applet still does not show up in "Add to Panel..."

Who can point out what I'm doing wrong?

---

