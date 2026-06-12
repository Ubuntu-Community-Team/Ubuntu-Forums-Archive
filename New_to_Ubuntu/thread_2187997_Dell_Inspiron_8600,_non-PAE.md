---
title: "Dell Inspiron 8600, non-PAE"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by shabuboy on 2013-11-15
Hello,

Due to playing aka learning, blew up previous install and will reinstall the OS. 

System: Dell Inspiron 8600, Pentium M 1.4mhz, 2gb RAM with GeForce Go5200 32mb video card. 
Usage: 3 nephews ages 6-9. Light, mainly to browse internet, youtube, learning games, homework, etc.

I would think a distro with LTS is better. Lubuntu 12.04 expired last month. 

So my questions are:
1- Lubuntu 12.04, security updates will be provided until 2017. What will not be covered? Apps such as internet browsers, games, etc?
2- What is the difference between Ubuntu 12.04 with  a light desktop manager (xfce/lxde) vs Lubuntu 12.04?
3- What would you recommend?

Added: Need to stick with 12.04 release due to NON-PAE CPU (read [this]("http://ubuntuforums.org/showthread.php?t=2130640&highlight=lubuntu+xfce")). Found out the hard way.

---

### Post by fantab on 2013-11-15
Lubuntu 12.04 is NOT an LTS.
[QUOTE=https://wiki.ubuntu.com/Lubuntu]ubuntu 12.04 is not an [LTS]("https://wiki.ubuntu.com/LTS") (5  years support), but a standard release that is supported for 18 months  (if you would like to change this please feel free to contact the  developers to offer assistance in this area).[/QUOTE]

I think you should stick with Ubuntu, perhaps Xubuntu (Xfce). The difference is in the default apps, Desktop interface and the consumption of resources.

What you can do?
Install Ubuntu 12.04
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

Then Install Xfce, so you have both Unity, and Xfce. You can choose which one you want from Login box (right-hand top gear icon will help you choose which).

To install just [Xfce]("http://www.xfce.org/") check out the [Screenshots]("http://www.xfce.org/about/screenshots") to know the difference
```
sudo apt-get install xfce4
```

Or 

Install the whole Xubuntu-desktop (this comes with all the default applications), you might end up using two similar applications one from Ubuntu and one from Xubuntu. For instance, you will have two file-browsers, Nautilus from Ubuntu and Thunar from Xubuntu.

```
sudo apt-get install xubuntu-desktop
```

Good Luck

---

### Post by mörgæs on 2013-11-15
> **shabuboy said:**
> 
Need to stick with 12.04 release due to NON-PAE CPU (read [this]("http://ubuntuforums.org/showthread.php?t=2130640&highlight=lubuntu+xfce")). Found out the hard way.

Your hard way was not the right way. Please read about [PAE]("https://help.ubuntu.com/community/PAE") here. 

X/Lubuntu is a better choice than Ubuntu for old hardware.

---

### Post by shabuboy on 2013-11-15
Yes I tried the mini.iso and it hangs right after the proxy window. Empty big pink screen with a white bar at bottom, 1hr later no changes.

But still, can someone tell me in plain English what is the worst case scenario if I stay with Lubuntu 12.04 which support expired last Month? The more I read about LTS, the more confuse I get.


BTW: I have tried Puppy, kept crashing under normal usage after install. Mint 13 cinnamon and xfce crashed during install. Ubuntu got the PAE CPU error.

The only ones that have worked, xubuntu and lubuntu 12.04. Last time installed lubuntu, installed ubuntu-desktop, removed lubuntu, added xfce. But kept playing with it and trying different things until broke it. Now, after all the experiences feel I can do the final install before passing it to my nephews. Except for the questions on the first post.

---

### Post by mörgæs on 2013-11-15
An unsupported version is a security breach. When a bug is found there will not be any fixes for it, so people might steal sensitive information, for example. 

How does a fresh install of Bodhi or Xubuntu 12.04 work?

---

### Post by shabuboy on 2013-11-15
Got it, not sure if that is a major concern, since the kids will be using it. Don't believe they have bank, investment or email accts. But will check with their Momma. hmmm wonder if she will be using it... Anyhow, I just discovered ubuntu-edu-primary package (aka Edubuntu), it rocks!!! Perfect for what she wanted. Installed on Lubuntu 12.04.

Yeah, will try those two next. Thank you for the suggestions!

To be continue...

---

### Post by shabuboy on 2013-11-18
Well, Bodhi install ran fine. It even found the wireless drivers. 
Anyhow, seems to be working fine, not too crazy about the Enlightenment window manager though... This will go to a non-tech Mom and kids who are used to drag/drop. Creating simple desktop items is confusing. Nice to the eyes though.
Still testing it...

Haven't try Xubuntu. But I am running out of time. 

One more thing... Beside the obvious, what is the main difference between:
Ubuntu 12.04 + xfce4 (bloated, unity, 5 yr LTS)
vs
Xubuntu 12.04 (xfce4, dups apps, 3 yr LTS)

---

### Post by yc.chenyi on 2013-11-18
Ubuntu 12.04 LTS will be supported in a long time. 
Try using Ubuntu instead of Lubuntu, but you can install Lxde for your own flavor. There are no big differences.

Considering your hardware, you can try some lightweight desktop environments such as Xface.
Don't worry about the security updates, man. 
Few hackers would like to pay their attention on Linux, and in most cases the updates are for new features.
I was using 10.04 three weeks ago on my old laptop.

---

### Post by mörgæs on 2013-11-18
> **yc.chenyi said:**
> 
Don't worry about the security updates, man. 
Few hackers would like to pay their attention on Linux, and in most cases the updates are for new features.
I was using 10.04 three weeks ago on my old laptop.

What you do on your own computer is personal business, but please don't encourage others to neglect security.

---

### Post by mörgæs on 2013-11-18
> **shabuboy said:**
> 
Beside the obvious, what is the main difference between:
Ubuntu 12.04 + xfce4 (bloated, unity, 5 yr LTS)
vs
Xubuntu 12.04 (xfce4, dups apps, 3 yr LTS)

The first combination would only be supported for three years on the XFCE parts meaning that the system as a whole has only the same three years.

Which desktop environment you prefer is mostly a matter of taste (and the capabilities of the hardware in question).

---

### Post by shabuboy on 2013-11-18
hmmm, sorry for all the questions... First combo only 3yrs? Don't get it, I think I am missing something...
Unless... xfce = Xubuntu, no matter whether you install from the Xubuntu IOS or via Ubuntu (xfce and/or desktop). Is that so?

Yeah, it sure has been an experience on the desktop part/window managers. Never imaged there were so many options!

---

### Post by fantab on 2013-11-18
> **shabuboy said:**
> hmmm, sorry for all the questions... First combo only 3yrs? Don't get it, I think I am missing something...
Unless... xfce = Xubuntu, no matter whether you install from the Xubuntu IOS or via Ubuntu (xfce and/or desktop). Is that so?

Yeah, it sure has been an experience on the desktop part/window managers. Never imaged there were so many options!

Welcome to Linux, the world of 'true' choice. Sometimes so many options can really confuse you. I guess this is one of the reasons why most longtime Linux users end with multiple distros on their systems. I have three: Ubuntu-Unity, Arch-Gnome-Shell and Fedora-Xfce. I like all three and can't just pick one and commit. 

Xubuntu is supported as LTS for 3yrs. Well, lets just say its the choice of Xubuntu developers/packagers/maintainers. Ubuntu too used to be 3yrs. LTS. The Ubuntu team only recently, from 12.04, decided to go with 5yrs. support for LTS. On the other hand, Lubuntu does NOT have LTS support. 
Yes, they are all Ubuntu with a different 'desktop'.

Since you are trying desktops, allow me to suggest to you [CRUNCHBANG]("http://crunchbang.org/"). It too is light weight distro with OPENBOX on [*DEBIAN*]("http://www.debian.org/").

---

### Post by stucazedmacca on 2013-11-19
Have you tried Lubuntu [http://www.lubuntu.net/](http://www.lubuntu.net/)

11.10 instals on a non pae system 12.04 also i think but ive used 11.10 recently on a few old laptops and they work great very fast now for some kids the same age.

---

### Post by sudodus on 2013-11-19
> **shabuboy said:**
> hmmm, sorry for all the questions... First combo only 3yrs? Don't get it, I think I am missing something...
Unless... xfce = Xubuntu, no matter whether you install from the Xubuntu IOS or via Ubuntu (xfce and/or desktop). Is that so?

Yeah, it sure has been an experience on the desktop part/window managers. Never imaged there were so many options!

... and I can add even more options:

- Install a system with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"). You can try several systems based on Ubuntu 12.04 LTS or a new Lubuntu 13.10 system which works thanks to [fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE").

- See also the first and several of the latest posts in this thread [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by sudodus on 2013-11-19
> **stucazedmacca said:**
> Have you tried Lubuntu [http://www.lubuntu.net/](http://www.lubuntu.net/)

11.10 instals on a non pae system 12.04 also i think but ive used 11.10 recently on a few old laptops and they work great very fast now for some kids the same age.

Lubuntu 11.10 works well on old hardware but has passed end of life long ago and receives no security updates.

---

