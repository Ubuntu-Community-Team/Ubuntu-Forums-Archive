---
title: "Fixing ATI fglrx max/min window issue"
date: 2010-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by sandyd on 2010-04-17
Theres been a lot of issues with maximizing/minimizing windows when using the fglrx drivers.
This was caused by a edit to xorg that would improve intel card performance, so only do this if your have an ATI card, and you are using fglrx.

so lets begin...
we will first need to download the Xorg-Server source code and download its compiling dependencies.
```

mkdir ~/dev/
cd ~/dev
apt-get source xorg-server
cd xorg-server*
cd composite

```
we will now need to edit the code. Replace 'kate' with 'gedit' if you are using gnome and have these issues.
```

kate compalloc.c

```
search for the line
```

pPixmap->screen_y = y;
```
comment out everything under there, up to and excluding the line
```

return pPixmap;
```
you can do this by using /* to start a comment, and */ to end a comment (Careful, there is a comment in the middle of the stuff you need to comment out, and it will interfere with your commenting.

then, run thi
```

cd ../
debuild

```
Ignore the warning about it not being able to sign.
```

cd build-main
sudo apt-get install
```
You should now have faster fglrx performance

---

