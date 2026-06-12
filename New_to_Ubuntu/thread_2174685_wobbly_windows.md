---
title: "wobbly windows"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by sedoy on 2013-09-15
I have ubuntu 13.04 with gnome 3.8
I have installed compiz, CCSM.. I`m activated Wobbly windows on it but they doesnt work
HOW
I need it, I like it

---

### Post by Y^2om&amp;#7sgP on 2013-11-29
I'm running Xubuntu 12.04 (fresh install) and followed

[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

All looked good, but wobbly windows doesn't work.

Anyone?

---

### Post by Frogs Hair on 2013-11-29
Wobbly Windows work in Unity for me (13.10) ,  but won't work in the Gnome Shell because it uses the Mutter window manager and not Compiz . To enable them in Unity disable snapping windows and enable wobbly windows.

---

### Post by jimmyh1972 on 2013-12-05
Woobly is available in ubuntu versions 11 and above only in unity desktop (unfortunately...)
in any other desktop enviorment (such as cinnamon , gnome , xfce etc.) it won't work

---

### Post by stinkeye on 2013-12-05
You can use compiz as the window manager in an xfce session .... including wobbly windows.
As well as the default compiz packages check you have the **compiz-plugins** package.

In xfce....
```
compiz --replace & disown
```

Switch back....
```
xfwm4 --replace & disown
```

---

### Post by monkeybrain20122 on 2013-12-05
> **sedoy said:**
> I have ubuntu 13.04 with gnome 3.8
I have installed compiz, CCSM.. I`m activated Wobbly windows on it but they doesnt work
HOW
I need it, I like it

Wobbly windows works very well in Unity.Gnome shell doesn't use Compiz, it has its own compositer, so your approach is not going to work.

In Gnome shell there is a wobby window extension. [https://extensions.gnome.org/extension/669/wobbly-windows/](https://extensions.gnome.org/extension/669/wobbly-windows/)

But it works very  poorly on my system with a lot of tearing even with their work around (had tried it with Fedora, Debian and Manjaro and both with the Nvidia driver and the free one). It is not nearly as smooth as the Compiz one.--well the screenshot is actually exactly whay it looks like. Maybe it is my  hardware, you can try if you want.

---

### Post by monkeybrain20122 on 2013-12-05
> **hattpa said:**
> I'm running Xubuntu 12.04 (fresh install) and followed

[http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

All looked good, but wobbly windows doesn't work.

Anyone?

I have no idea that it is so compilcated to set it up in Xubuntu. I have a partition running Manjaro Linux with xfce and setting up compiz is a piece of cake: Install from AUR, set fusion icon to autostart and that's it. I think it is a bad idea to run compiz on any *buntu flavour except for the default Unity DE because all *buntu ship with compiz 0.9X in the repo which is made with unity in mind. To make compiz work with Unity new bugs and regressions were introduced and unless you are using unity all these could be avoided by using the 0.8* branch (which is what I got from AUR)

BTW, KDE also has wobbly windows (and cube) and it works well.

---

