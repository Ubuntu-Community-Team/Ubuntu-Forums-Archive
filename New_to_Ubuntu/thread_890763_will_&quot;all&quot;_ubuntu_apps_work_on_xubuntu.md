---
title: "will &quot;all&quot; ubuntu apps work on xubuntu ?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-08-15
im installing xubuntu on my dads pc in a week. i was told because of his slow system specs this would be a good choice. my question is will all ubuntu applications work on xubuntu ? i want to give him the best experience he can have with linux.

---

### Post by Martje_001 on 2008-08-15
No, compiz-fusion (and maby some others) will not work. The rest will work fine though.

---

### Post by Steveway on 2008-08-15
> **Martje_001 said:**
> No, compiz-fusion (and maby some others) will not work. The rest will work fine though.

What the heck are you talking? Compiz-fusion and everything else will of course work. It doesn't matter what Desktop-environment you are using.

---

### Post by snowpine on 2008-08-15
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

---

### Post by lukjad on 2008-08-15
I don't think that all of the same exact ones will run but at the very least most of the major ones will have similar apps. I used Xubuntu and I didn't miss much. (Maybe a game or two.)

---

### Post by smooth3006 on 2008-08-15
i guess what im asking is when i install it does it have the same default apps installed that ubuntu does minus the different desktop environment. im going to be using that multimedia guide on this site for him and i want to make sure all of those apps will work. i read something about most gnome apps won't work with xubuntu, is that true ?

---

### Post by snowpine on 2008-08-15
> **smooth3006 said:**
> i guess what im asking is when i install it does it have the same default apps installed that ubuntu does minus the different desktop environment. im going to be using that multimedia guide on this site for him and i want to make sure all of those apps will work. i read something about most gnome apps won't work with xubuntu, is that true ?

Ubuntu and Xubuntu have different default apps, that is true. However, you can add apps using several methods (add/remove programs, synaptic, command line) and Xubuntu and Ubuntu use exactly the same repositories.

---

### Post by aysiu on 2008-08-15
All of them will run, but if you run too many Gnome applications, you might as well use Gnome.

I can't imagine someone would want to run the Gnome panel and Nautilus on Xubuntu, and then expect to get the kind of performance you would normally get frmo Xfce without those programs.

Which applications in particular were you worried about?

---

### Post by tangibleorange on 2008-08-15
Xubuntu has different packages installed by default It has firefox, thunderbird, Abiword, Gnumeric etc.. However, all Ubuntu (GNOME) apps can be installed PROVIDED you are willing to install gnome libraries (this will take up a fair bit of disk space, especially on an older PC, and will happen automatically if you install a GNOME application). some may not work correctly and may be buggy, look ugly, or be very slow however. if you put a -gtk after the packagename, this can sometimes work. eg:

firefox in ubuntu: package firefox
firefox in Xubuntu: package firefox-gtk

not all packages have the -gtk option. I know openoffice.org and firefox do...

---

### Post by smooth3006 on 2008-08-15
> **snowpine said:**
> Ubuntu and Xubuntu have different default apps, that is true. However, you can add apps using several methods (add/remove programs, synaptic, command line) and Xubuntu and Ubuntu use exactly the same repositories.

thanks that's what i needed to know. i run ubuntu x64 on my pc. my dads computer is pretty slow and xp really bogs it down. 

here is a list of what i will be installing for him :

multimedia guide on here "flash, java, etc."
envy / nvidia drivers
encyclopedia brittanica linux
avant window navigator?
hp printer drivers
avast linux edition scanner
gufw firewall interface for iptables
adobe reader
wine
transmission
open office / i have been told abiword & gnumeric might be a better choice for him ?

here are his pc specs: pentium 3 / 750mhz. 512mb ram & 40gb hdd.

---

### Post by tangibleorange on 2008-08-15
that should all be fine. just install as you would on ubuntu.

Abiword and Gnumeric are installed by default on Xubuntu. They work fine for most purposes, but some people prefer openoffice. In xubuntu, be sure to install the gtk version:

```
sudo apt-get install openoffice.org-gtk
```

also xubuntu has its own version of the restricted extras package: xubuntu-restricted-extras

APTly named! ahaha that's not funny...

---

### Post by Paqman on 2008-08-15
> **aysiu said:**
> All of them will run, but if you run too many Gnome applications, you might as well use Gnome.


I'm inclined to agree.

Personally i've found that the difference in performance between XFCE and Gnome isn't a heck of a lot, and that the extra features in Gnome are well worth having. Nautilus is a much, much better file manager than Thunar, for example.

As for Compiz, XFCE actually has it's own compositor built in, so you can get a lot of nice features (dropshadows, ability to run AWN, etc) without needing Compiz at all.

---

### Post by durundal on 2008-08-15
I've had minor problems running some applications under wine and some programs designed for KDE have buggy gui's, but other than that every application I've used in xubuntu runs fine.  

In a lot of cases the programs will run a lot faster on my slow computer using xubuntu, I would even go so far as to say that if you don't install xubuntu it will give your dad a bad linux experience.

---

### Post by lukjad on 2008-08-15
> here are his pc specs: pentium 3 / 750mhz. 512mb ram & 40gb hdd.

I am running Hardy Heron 8.04 on just a bit more RAM and less of everything else. you may be able to install Hardy, depending on the brands of hardware installed.

---

### Post by aysiu on 2008-08-15
With a 40 GB hard drive, you could easily install both Ubuntu *and* Xubuntu, so you will have all of their programs available, regardless of what desktop environment you're currently logged into.

You may also want to consider [IceWM](http://www.psychocats.net/ubuntu/icewm).

---

### Post by snowpine on 2008-08-15
> **smooth3006 said:**
> thanks that's what i needed to know. i run ubuntu x64 on my pc. my dads computer is pretty slow and xp really bogs it down. 

here are his pc specs: pentium 3 / 750mhz. 512mb ram & 40gb hdd.

Those specs are not that bad. :) Openoffice will run just fine; I know because I use it on my 600mhz P3 with 384mb of ram and a 6gb hard drive. It's a little slow but not terrible.

Basically to clarify what others are saying, the default apps that come with Xubuntu will be the fastest and most efficient, because all of the "dependencies" will already be installed with the system. However, if you need to use a Gnome or KDE application for which there is no Xubuntu alternative, you can certainly do so--it will be slightly "bloated" (due to installing all of the dependencies) but nothing to worry about.

---

### Post by decoherence on 2008-08-15
The only issue with installing software intended for another desktop environment is that often chunks of that environment have to be installed as well, which can disproportionately increase your resource usage.

This is more of an issue between Kubuntu and Ubuntu. They don't share as many components as Xubuntu and Ubuntu so more redundant things get loaded.

---

### Post by aimpau on 2008-08-15
I've been running my own home blend of Xubuntu studio/electronic workbench with my GF's old laptop (PIII, 450Mhz, 128 RAM, 6GB)

try these packages:

gimp
seq24
mpd
mpc
cdcd
timidity
jack
jackbeat
tk707
xine
phatch
avidemux-gtk
MPLAB -wine
qucs
gpsim
eagle

Most of these runs on tk/tcl (not GTK or GNOME) which, I think, are faster(er).

enjoy your xubuntu!

---

### Post by smooth3006 on 2008-08-15
well alot of poeple tell me xubuntu would be best with his system specs so ill go with that for now. im sure all of the apps i listed should work ok? im not going to install both ubuntu & xubuntu as he will already be dual booting with his xp install until he gets used to linux.

---

