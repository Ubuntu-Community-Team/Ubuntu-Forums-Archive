---
title: "Thinkering with Xubuntu on an OLD LAPTOP!"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Mudguard on 2008-11-27
Hello, this is my first form posting... I'm a realative newb to Ubuntu and Linux etc. 
I've got an old Fujitsu siemens laptop with a 1Gb processer and 128mb of ram and i've been trying to find the best Operating System for it! I've tried various older Ubuntu and Xubuntu versions but its very slow for them all, tried Damn Small Linux, it was rocket fast, and on the internet too! But i couldn't get my head around setting up the usb port so i'm back to the drawing board now! I want to set up a light ubuntu system! if anyone has any suggestions on this front they'd be very welcome..

So i've just installed Xubuntu 8.10 and i've installed the command line system, now i've been  following some of the instructions on:

 [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

but i've got a few basic issues with it..
like when you've installed the system, how do you install the Graphic User Interface!?
Or is it always goin to be a command line system!
Do those extras such as adding a Window Manager, Login Manager, File Manager etc. make up the graphic user interface!?
Is this a good way of building up a basic operating system for an old laptop!

---

### Post by halitech on 2008-11-27
if you have the basic command line system already installed, just type in
```
sudo apt-get install xubuntu-desktop
```which will give you a typical xubuntu install. if you want a littl more control, check here

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

just start with step 7 and work down

---

### Post by Kevbert on 2008-11-27
With those specs, it may be better to try something like [[COLOR="Red"]Puppy[/COLOR]]("http://www.puppylinux.org/") or [COLOR="Red"][Slax]("http://www.slax.org/")[/COLOR] instead.

---

### Post by laurielegit on 2008-11-27
Well this will give you a minimal Xubuntu install:

```
sudo apt-get update
sudo apt-get install xorg xterm gdm xfce4 menu firefox gksu synaptic
sudo /etc/init.d/gdm start
```

It will install the xfce4 window manager. If you need more add on their pacage name to the end of the list. E.G.

```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic **flash-nonfree pidgin amarok** 
sudo /etc/init.d/gdm start
```

That will install the same as the former, but will incude the flash plugin for firefox, the pidgin internet mesanger and the amarok media player.

Post back here if you need more help. Good luck,

Laurie

---

### Post by Mudguard on 2008-11-27
Cheers laurielegit, think thats what i was lookin for i'll get on to that so next time i'm on a cat5 internet...

---

### Post by frankleeee on 2008-11-27
I have a laptop with a 1 gig chip but 512 ram and it runs Ubuntu and Xubuntu pretty fast, you might consider upping you ram it is a pretty cheap way of getting where you want.

---

### Post by ugm6hr on 2008-11-27
This is a useful reference for Ubuntu-based custom distros...
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

It offers even lighter options:
e.g. wdm rather than gdm, lighter web-browsers.

Also, consider using lxde (instead of xfce) as the desktop environment, since it is even lighter - it includes pcmanfm, which I am sure automounts USB devices (from memory).  I have only dabbled with it, on top of a standard Gnome install (so uncertain what component does what!)

---

### Post by 2blue on 2008-12-15
I agree with frankleeee. I found two new memory cards very cheaply on ebay, and everything runs faster on my old laptop. Your processor is rather good for an old laptop and your RAM will most likely make a difference. It did for my laptop which is really old with a smaller processor than yours. It runs Xubuntu not that much slower than Puppy or DSL.  

Others have mentioned Puppy Linux, it is very light and if you are lucky it will install pretty easy on your machine. Well worth trying.

---

### Post by Harii on 2009-01-17
I would go with debian/ubuntu based distro because puppy and dsl are limited on apps.  I would go with debian minimal install over them.
 lxde is a good choice but xfce will work with them specs.

try antix-mepis or crunchbang linux:popcorn:

---

### Post by lswb on 2009-01-17
> **frankleeee said:**
> I have a laptop with a 1 gig chip but 512 ram and it runs Ubuntu and Xubuntu pretty fast, you might consider upping you ram it is a pretty cheap way of getting where you want.

Agreed 100%. I have an old Pentium 3 650Mhz laptop. It is maxed out at 512 MB ram (Most Pentium 3 systems can accept a max of 512, a few could use more) and it runs ubuntu/gnome just fine. A 1Ghz processor with adequate ram will run any current linux desktop distrubution.

---

