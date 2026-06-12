---
title: "Removing GNOME"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by tomor on 2008-04-25
Hi, 

I want to remove gnome as a desktop environment but not necessarily applications such as firefox or openoffice. Could you give me a brief explanation how to do this?

Thanks.

---

### Post by Paqman on 2008-05-15
You can use the instructions on Psychocats about setting up [Pure KDE](http://www.psychocats.net/ubuntu/purekde). Just remove any Gnome apps you want to keep from the list.

---

### Post by takuhii on 2008-05-15
you could try 'sudo apt-get remove ubuntu-desktop', just to be on th esafeside run 'sudo apt-get install kubuntu-desktop'. Without the marks round it of course ;)

---

### Post by bodhi.zazen on 2008-05-15
IMO it is best to perform an minimal install then build up.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/](http://kmandla.wordpress.com/2007/04/01/feisty-openbox-on-1ghz-pentium-iii-start-to-finish/)

Then, if you want KDE / XFCE / Gnome, install the DE as packages and not desktop

ie install KDE not kubuntu-desktop.

[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835&highlight=Lightweight+gnome")

Or go for an alternate window manager such as Fluxbox, Openbox, IceWM, PKWM ...

---

### Post by stchman on 2008-05-15
> **tomor said:**
> Hi, 

I want to remove gnome as a desktop environment but not necessarily applications such as firefox or openoffice. Could you give me a brief explanation how to do this?

Thanks.

The package ubuntu-desktop is a meta package with things like openoffice and firefox attached to them.

My advice if you really want KDE over Gnome then install Kubuntu.

---

### Post by Oldsoldier2003 on 2008-05-15
I agree with Bodhi, I've been building some minimal systems for live cd installs lately and the best method I have found so far is to use the minimal install and then add xorg and the base window manager. Then from there just add in the apps you want. Its a little trickier in Ubuntu than it is in Debian (especially if you want gnome) but your install will be leaner and meaner.

---

