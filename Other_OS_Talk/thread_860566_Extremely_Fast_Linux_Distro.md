---
title: "Extremely Fast Linux Distro"
date: 2008-07-15
forum: Other OS Talk
---

### Post by patrickaupperle on 2008-07-15
I am looking for an extremely fast OS. Right now I am trying Arch, but I can not get xorg to work right. I was wandering what other really fast OSes are out there. My requirements are:
 1: Package management
 2: Automatic Dependency resolution
 3: Graphical Desktop (not necessarily in the default install)
 4: I have to be able to install it. I would consider myself fairly proficient with linux.

---

### Post by kerry_s on 2008-07-15
debian custom, use the net installer to install a base and build from there, i do all mine that way.
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso)

---

### Post by Joeb454 on 2008-07-15
I'm considering doing a debian custom install on a server sometime, how simple is it?

---

### Post by patrickaupperle on 2008-07-15
> **kerry_s said:**
> debian custom, use the net installer to install a base and build from there, i do all mine that way.
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso)

What do you suggest?
KDE, Gnome, XFCE, LXDE, or other?

---

### Post by cardinals_fan on 2008-07-15
Vector Light.

---

### Post by patrickaupperle on 2008-07-15
> **cardinals_fan said:**
> Vector Light.

That did look nice. I tested it and the normal vector in VBox and they perform very similarly. In fact Gimp, I installed it myself in both, launches faster in normal Vector. Also, There repos are limited and I can not get slapt-get to work.

---

### Post by VCSkier on 2008-07-15
I've heard that for an out of the box experience, Sidux can't be beat on speed.

---

### Post by patrickaupperle on 2008-07-15
is Net install debian + apt-get install xorg gnome lighter then regular debian?

---

### Post by kerry_s on 2008-07-15
> What do you suggest?
KDE, Gnome, XFCE, LXDE, or other?

lighter, use a window manager for speed. fluxbox, openbox and icewm are some of the most popular. i use jwm.


> is Net install debian + apt-get install xorg gnome lighter then regular debian? 

net install, but no gnome, if your going to use gnome you might as well get the full install.

with the net install, when it gets to package selection uncheck everything, that will give you just a base to build on. 

after reboot just log in as root and apt-get what you want, here's a example of what i might do:

apt-get install xorg synaptic jwm menu
update-menus
exit

log in as regular user:
startx
open synaptic and continue building

---

### Post by init1 on 2008-07-15
> **patrickaupperle said:**
> I am looking for an extremely fast OS. Right now I am trying Arch, but I can not get xorg to work right. I was wandering what other really fast OSes are out there. My requirements are:
 1: Package management
 2: Automatic Dependency resolution
 3: Graphical Desktop (not necessarily in the default install)
 4: I have to be able to install it. I would consider myself fairly proficient with linux.
I recommend SliTaz. When it's run from RAM, apps load almost instantly so I assume that it runs fast from a hard drive too. 
[www.slitaz.org/en](www.slitaz.org/en)
The package manager is called tazpkg and does indeed resolve dependencies.

---

### Post by AnLGP on 2008-07-15
debian base install and slitaz are both good.

---

### Post by wolfen69 on 2008-07-15
put puppy linux on anything with 700mhz or better, and when you click something, it will open *yesterday*. lightning speed without having to "build" a distro.

---

### Post by oldos2er on 2008-07-16
> **patrickaupperle said:**
> That did look nice. I tested it and the normal vector in VBox and they perform very similarly. In fact Gimp, I installed it myself in both, launches faster in normal Vector. Also, There repos are limited and I can not get slapt-get to work.

 Use "su" to log in as root, then run slapt-get. Or just use the Gslapt package manager (similar to Synaptic).

---

### Post by kpkeerthi on 2008-07-16
> **patrickaupperle said:**
> Right now I am trying Arch, but I can not get xorg to work right. 

The easiest fix would be to use xorg.conf from Ubuntu Live CD (if that worked).

---

### Post by patrickaupperle on 2008-07-16
> **kpkeerthi said:**
> The easiest fix would be to use xorg.conf from Ubuntu Live CD (if that worked).

It was  not that type of problem. I could not get startx to work. I modified .inintrc, I think, to include exec startlxde and it worked. Thank you of the solution though.

---

### Post by darrelljon on 2008-07-16
> **patrickaupperle said:**
> What do you suggest?
KDE, Gnome, XFCE, LXDE, or other?
Fluxbox, Enlightenment, JWM.

---

### Post by tommcd on 2008-07-16
> **patrickaupperle said:**
>  My requirements are:
 1: Package management
 2: Automatic Dependency resolution
 3: Graphical Desktop (not necessarily in the default install)
 4: I have to be able to install it. I would consider myself fairly proficient with linux.

Try Zenwalk: [http://zenwalk.org/](http://zenwalk.org/)
1 and 2. Zenwalk's package manager is called netpkg. It is reliable and does resolve dependencies. Zenwalk does not have the vast number of packages available in Debian / Ubuntu repos, but there are packages available for just about anything you would ever want to do, and the packages are up to date and are stable.

3 and 4. Zenwalk has a very simple text based installer. You will find it to be mostly automatic and much easier than Arch. It is easy to use and installs fast (about 15 minutes) The default install boots to a graphical desktop.

Zenwalk is based on Slackware. It uses XFCE desktop by default. There are KDE and Gnome desktops available on the Zenwalk repos also. Zenwalk is much lighter on system resources than Ubuntu. Read through the Zenwalk manual to get started: [http://manual.zenwalk.org/en/](http://manual.zenwalk.org/en/) 
The Zenwalk companion has a detailed description of all the programs available in Zenwalk's repos: [http://wiki.zenwalk.org/index.php?title=Index:Zenwalk_Companion](http://wiki.zenwalk.org/index.php?title=Index:Zenwalk_Companion)

---

### Post by K.Mandla on 2008-07-17
I would second most of the distros already mentioned here. Debian was surprising to me, for as fast as it was. I honestly anticipated it would be as sluggish as Ubuntu, but it's very perky, and behaves like you might expect if you've spent much time with Ubuntu.

Arch is still the fastest precompiled distro for me. It does take some configuring though. Beyond that, I swear by Crux. It's ungodly fast. :twisted:

---

### Post by CJ56 on 2008-07-18
I would second Tommcd - Zenwalk is very easy to install, has a reasonable package management setup (a lot better than it used to be) is dead stable and very quick. Xfce goes like the clappers and is nice to use if you like that kind of thing. Forums are helpful, too.

---

### Post by patrickaupperle on 2008-07-18
I ended up choosing arch. I also ended up using KDE :lol:. KDEmod actually. It looks great and performs better then xubuntu, for me anyway. The one thing I need to fix is that konqueror won't spell check.

---

### Post by eternalnewbee on 2008-07-18
Hi there.
I've just finished installing Linux TLE on an old , very slow computer.
Linux TLE is a Thai distribution based on Ubuntu Gutsy. I'm not as much looking for a fast distro as I am for a window manager that's light and compatible.
I've installed fvwm and it works fine, except that I can't open any open office apps even though they are there...
Any help would be great. Thanks

---

### Post by patrickaupperle on 2008-07-18
> **eternalnewbee said:**
> Hi there.
I've just finished installing Linux TLE on an old , very slow computer.
Linux TLE is a Thai distribution based on Ubuntu Gutsy. I'm not as much looking for a fast distro as I am for a window manager that's light and compatible.
I've installed fvwm and it works fine, except that I can't open any open office apps even though they are there...
Any help would be great. Thanks

Have you tried LXDE? I used it for a while, but don't really need something light. It's nice.
[http://lxde.org/](http://lxde.org/)
[http://lxde.org/wiki/Ubuntu](http://lxde.org/wiki/Ubuntu)

p.s. I don't know if your distro is compatible with ubuntu repos, but if it is follow the instructions in link 2.

---

### Post by Dr Small on 2008-07-18
As K.Mandla said, ArchLinux or Crux.

---

### Post by eternalnewbee on 2008-07-18
Thanks patrickaupperle. Will let you know the result.

---

### Post by eternalnewbee on 2008-07-18
Thanks Dr Small, but I specifically need Linux TLE

---

### Post by steveneddy on 2008-07-18
I prefer regular Ubuntu with Fluxbox as the DE.

I find this setup snappy and responsive, but not as fast as Puppy.

---

### Post by Twitch6000 on 2008-07-19
> **kerry_s said:**
> debian custom, use the net installer to install a base and build from there, i do all mine that way.
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso)

Darn you... Now I am distro hopping again.I thought I was settled down with PClinuxOS :(.

---

### Post by fwojciec on 2008-07-19
The recent "most fastest" configuration -- Arch 64bit with standalone Compiz-Fusion, used kind of like one uses *boxes, and the vast majority of anmations/fluff disabled.  3d rendering seems to be *much* faster on my system than 2d rendering (what's wrong with the recent nvidia drivers?) -- so Compiz actually feels faster overall, and more robust somehow, than Openbox!?!

---

### Post by tel93 on 2008-07-20
> **kerry_s said:**
> debian custom, use the net installer to install a base and build from there, i do all mine that way.
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-netinst.iso)

Agreed

---

