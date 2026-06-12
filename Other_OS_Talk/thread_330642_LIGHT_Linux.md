---
title: "LIGHT Linux"
date: 2007-01-03
forum: Other OS Talk
---

### Post by xArv3nx on 2007-01-03
Hello.

I've tried several distros, but can't seem to find a good, lightweight one. I'm on an OLDER computer for a while until I get my new one fixed. Any ideas?

**_System_**

AMD Athlon XP 2200+ @ 1800mghz
256 MB of RAM
GeForce 6600 GT (Which Ubuntu does a horrible job of recognizing, btw.)

It can be a relatively large distro, because I DO have a DVD burner, but it can't be Ubuntu. Ubuntu tends to lag my system. I've tried the Christmas Edition, Mint, and just plain Ubuntu. Both have lagged pretty bad.

Thank you VERY much.

---

### Post by aysiu on 2007-01-03
That kind of system doesn't need a lightweight distro. Any distro should run fine on that (in terms of resources).

Maybe you should try a non-Ubuntu Linux distro--it may detect your hardware better. Try PCLinuxOS, Mepis, Fedora, or OpenSuSE.

---

### Post by meng on 2007-01-03
(Christmas? You mean Christian perhaps?)
Okay what about:
Xubuntu (xfce is lighter than GNOME)
Fluxbuntu (fluxbox is even lighter)
Damn Small Linux (if you don't mind using kernel 2.4.x)
Puppy Linux
Feather Linux

all should be available as live distro.

And (just in case) remember that live distros will run slower than installed ones. Not meaning to insult your intelligence, but it's often better to state the obvious than assume it's known.

AND: what is lagging? is it graphics that is lagging (because you can solve that by installing proprietary nvidia drivers)

---

### Post by ZylGadis on 2007-01-03
What is old about this system? It's perfect, just needs a bit more RAM perhaps.

If you want to stay with ubuntu: install the ubuntu server edition, which has no GUI and will drop you into a console. When that happens, just

```
sudo apt-get install xubuntu-desktop
```

and you're done. XFCE is much more lightweight than Gnome, not to mention KDE.

I don't believe Gnome would lag on that machine, though. I had the same CPU with 512RAM in one of the boxes at home and it worked great.

If you'd rather get away from ubuntu, the options are numerous.

---

### Post by xArv3nx on 2007-01-03
Alright, I think I'll try to stick with Ubuntu. I don't know what is lagging my system, though.

I'll try what the guy above me said.

And, yes, I know the LiveCD is slower than the regular system. My problem is that whenever I try to install it, I have to reconfigure the xserver-xorg package with dpkg-reconfigure by going into the terminal. (CTRL + ALT + F1) Then whenever I get that working, it still looks horrible, 1/4 of the screen is black, I have a low resolution, I can barely complete the installation, it takes about 20-30 minutes (Not to mention the cursor doesn't show up, and this is all in safe graphics mode). THEN, when I'm done I install the nVidia drivers in recovery mode. It seems the more Ubuntu releases updates, the more problems I have.

---

### Post by celsofaf on 2007-01-03
Suggestion: Zenwalk. Very very fast and beautiful, almost no bloat, yet quite easy. Unless you don't like Xfce and LILO...

---

### Post by mips on 2007-01-03
Try Sabayon, you will be impressed.

---

### Post by finferflu on 2007-01-03
Stick with Ubuntu and install IceWM as windows manager. You will need a bit of customization to make it look acceptable to your eyes, but it's quick as light.

```
sudo aptitude install icewm icewm-themes
```

If you are looking for nice themes, just tell me and I'll point you to some :)

---

### Post by MetalMusicAddict on 2007-01-03
> **ZylGadis said:**
> What is old about this system? It's perfect, just needs a bit more RAM perhaps.
RAM is all you need. I have a GIG of RAM in a VERY similarly speced HTPC that runs Ubuntu-Edgy just fine.

If you cant do the RAM Id look at Fluxbuntu.

---

### Post by Rodneyck on 2007-01-03
Try dreamlinux...light, very fast and beautiful.

[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

---

### Post by RAV TUX on 2007-01-03
> **xArv3nx said:**
> Hello.

I've tried several distros, but can't seem to find a good, lightweight one. I'm on an OLDER computer for a while until I get my new one fixed. Any ideas?

**_System_**

AMD Athlon XP 2200+ @ 1800mghz
256 MB of RAM
GeForce 6600 GT (Which Ubuntu does a horrible job of recognizing, btw.)

It can be a relatively large distro, because I DO have a DVD burner, but it can't be Ubuntu. Ubuntu tends to lag my system. I've tried the Christmas Edition, Mint, and just plain Ubuntu. Both have lagged pretty bad.

Thank you VERY much.
**[[B]Wolvix Hunter** 1.0.5 | **Wolvix** GNU/Linux]("http://wolvix.org/node/379")[/B]



**[]("http://wolvix.org/")**

---

### Post by 3rdalbum on 2007-01-04
Zenwalk, DreamLinux, or Elive (you can install it).

---

### Post by willskills on 2007-01-04
I agree with one of the replies very strongly, get some more RAM!

A processor that quick, with that kind of GFX card cannot run anywhere near optimum with only 256mb RAM!

---

