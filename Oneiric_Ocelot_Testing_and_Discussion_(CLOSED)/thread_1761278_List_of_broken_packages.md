---
title: "List of broken packages"
date: 2011-05-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-05-17
Every few days I get some new packages that are broken. They have dependency issues or the configuration failed. In the most cases it's fixed within a day. But there are a lot of packages that need several days before they are fixed.

We can post these problems on launchpad but from my experience I know there is a high chance that such minor things will be overseen. I have even the experience after I posted here on natty testing some of such issues they was fixed in a few hours (maybe somebody who could fix it read it). And because these problems are very recently I thought about a thread that lists all of these problems.


I want to begin with a few broken packages:

avahi-daemon (fails on configuration)
dbus (fails on configuration)
libpurple0 (dependency issue)
pidgin (dependency issue)

---

### Post by ranch hand on 2011-05-18
I take it that you re using Update Mangler for updates.

This really is not much of a problem if you use some actual real package management tool like apt-get, aptitude or, if you want a gui, synaptic.  Synaptic will tell you the problems very easily.

---

### Post by Sworddragon on 2011-05-18
Only dependency issues can be detected from apt before the package is being installed but not configuring issues.

---

### Post by ranch hand on 2011-05-18
If you have "apt-listchanges installed you get the news and update information.  If you were using Debian you could install "apt-listbugs" an get all bugs against each package and their severity and effects.

Then there is the entirety of the dpkg arsenal at your disposal using apt-get, see "man dpkg".

You might also want to check the Ubuntu repo for the package "apt-dpkg-ref" in synaptic and check the description.  I hope it is there.  Mighty handy.

---

### Post by Sworddragon on 2011-05-18
This are unknown bugs so these tools are useless here. This thread is just a try to enhance the speed with the packages get fixed.

---

### Post by dino99 on 2011-05-19
> **Sworddragon said:**
> This are unknown bugs so these tools are useless here. This thread is just a try to enhance the speed with the packages get fixed.

the only way to "enhance the speed with the packages get fixed" is to propose a fix and hope it can be commited, everything else is called noise and its useless, and worst can slow down to get a fix due to bugs comments spamming

---

