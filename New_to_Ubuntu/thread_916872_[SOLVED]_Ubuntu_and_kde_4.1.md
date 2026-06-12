---
title: "[SOLVED] Ubuntu and kde 4.1"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by heiowge on 2008-09-11
I want to have a go at KDE 4.1 without destroying my Ubuntu hardy settings.  If I install it and have a play, will it cause me any problems to switch back?

Can I easily import things like my firefox bookmarks?

---

### Post by DFlame on 2008-09-11
I'd say the absolute safest option for trying KDE 4 would be to download a Kubuntu LiveCD and try it out there. No system changes and no mess :)

You can download an image here: [http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

I'm also pretty sure there's a way to try KDE4 in your current setup without using a LiveCD, but managing multiple desktop environments isn't my forte.

DFlame

---

### Post by heiowge on 2008-09-11
That'd work, but I'm looking to play with it for a couple of weeks, switching back and forth between desktops.

I've installed it in another machine and am intrerested, but that machine isn't really accessable all the time.

I want to play about with it on my main desktop for a while and tweek it here and there, to see how it compares with Gnome.  Then if don't like it, I can easily switch back.

---

### Post by heiowge on 2008-09-12
bump

---

### Post by tuxerman on 2008-09-12
Yeah, its possible if you install **kubuntu-kde4-desktop** with your package manager. It's around a 100 MB download for me. You will get the option of choosing your session during login. 
Have a happy KDE experience!

---

### Post by SunnyRabbiera on 2008-09-12
You can install the kubuntu desktop package and it should work with no issues.
Using KDE or Gnome are just different DE's not different OS's

---

### Post by tangibleorange on 2008-09-12
yep or you could use this command at a terminal:

```
sudo aptitude install kde4-core
```

to install pure KDE4, or:

```
sudo aptitude install kubuntu-kde4-desktop
```

to install Kubuntu KDE4. this version has all sorts of kde apps, but is a bigger download and will clog your menus more. i personally prefer kde4-core as it allows me to build a system with only the apps i need - for example i never use photo management software.

---

### Post by kansasnoob on 2008-09-12
Look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

of this great tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by heiowge on 2008-09-12
Cheers guys.  Now playing around with KDE 4.1  Gnome is unaffected.

---

### Post by SunnyRabbiera on 2008-09-12
> **heiowge said:**
> Cheers guys.  Now playing around with KDE 4.1  Gnome is unaffected.

as it should be, KDE doesnt overwrite any of the settings of gnome except maybe when you select KDM over GDM for your login manager.

---

