---
title: "problem w/ compiz"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fignig on 2008-05-05
so i had compiz installed and everything on it was working fine until i had some desktop resolution problems, i changed my xorg.conf file and apparently that effected the compiz b/c all of my settings and gone, and it doesn't even seem to be working, can someone give me an uninstall and how to reinstall command?

i saw somewhere that this was the uninstall phase:

sudo apt-get -y remove compiz-core desktop-effects

sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

sudo apt-get remove --purge compiz* libcompizconfig* -s

---

### Post by macaholic on 2008-05-05
I doubt it is compiz causing the problem if you were editing your Xorg, try reconfiguring it after you back it up to see what happens. ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fignig on 2008-05-05
> **macaholic said:**
> I doubt it is compiz causing the problem if you were editing your Xorg, try reconfiguring it after you back it up to see what happens. ```
sudo dpkg-reconfigure xserver-xorg
```

no i am not doing that thing again, i hate it. DO NOT sudo dpkg-reconfigure xserver-xorg EVER!~!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by graben3 on 2008-05-05
This sounds like you dont have the right driver and 3d accel is not enabled. try typing this in a terminal :

glxgears or if using something else than nvidia type aiglxgears

If you see gears turning and FPS is faster than 800FPS, then the problem must be something else

---

### Post by fignig on 2008-05-05
> **graben3 said:**
> This sounds like you dont have the right driver and 3d accel is not enabled. try typing this in a terminal :

glxgears or if using something else than nvidia type aiglxgears

If you see gears turning and FPS is faster than 800FPS, then the problem must be something else

pete@pete:~$ glxgears
24256 frames in 5.0 seconds = 4851.028 FPS
24175 frames in 5.0 seconds = 4835.000 FPS
24039 frames in 5.0 seconds = 4807.678 FPS

---

### Post by fignig on 2008-05-05
[size="6"]can Someone Please Just Give Me The Command To Uninstall All Of Compiz And Everything That It ****** Up, And I Need The Command To Fresh Install Compiz.[/size]

---

### Post by fignig on 2008-05-05
> **fignig said:**
> [size="6"]can Someone Please Just Give Me The Command To Uninstall All Of Compiz And Everything That It ****** Up, And I Need The Command To Fresh Install Compiz.[/size]

b/c i'm trying to use compiz and all of the options and "extras" are ******* up and not working, so pretty much it's doing nothing for me. is it just me, or is ubuntu hard to work w/ and horrible...

---

