---
title: "ISO Mounting"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-24
Hey everyone.


What is a good program to use for ISO mounting, I used to use Daemon Tools on windows, is there an equiv for Linux? 

Thanks :D

V

---

### Post by vanadium on 2008-09-24
No experience with it, but it seems that acetoneiso is a powerfull iso mounting/manipulation application. If all you need to do is mount the iso, the plain command prompt also does wonders:
```

mkdir ~/iso
sudo mount filename.iso ~/iso -o loop

```
This will mount the image file image.iso in a directory "iso" in your home directory.

---

### Post by styfle on 2008-09-24
Wow if its actually that easy then thats amazing.
I would test it out but I dont have any .iso files lol

---

### Post by r_borkow on 2008-09-24
if you want a graphical tool like "daemon tools" in windows use "gnome-mount"

---

### Post by _sAm_ on 2008-09-24
I guess you know, but if you want to see a movie stored as .iso or .img you can without the need to mount them if you use VLC.

---

