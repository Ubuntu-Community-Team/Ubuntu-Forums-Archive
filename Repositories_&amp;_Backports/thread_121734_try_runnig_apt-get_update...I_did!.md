---
title: "try runnig apt-get update?...I did!"
date: 2006-01-25
forum: Repositories &amp; Backports
---

### Post by closeyourwindows on 2006-01-25
so I am doing an update and here is my repository list:
```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy universe
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://wine.sourceforge.net/apt/ binary/
deb http://people.ubuntu.com/~doko/OOo2 ./
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```
the error I get is when I do any thing that involves apt-get, I get the message:
```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```
but this happens even when running apt-get update

any solutions. I have tried different repositories and still no change.

---

### Post by Adrian on 2006-01-25
> any solutions.
Mirrormax is obsolete (and so are probably the other mirrors you've tried). Check out this document by Aysiu for a solution:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Sparkalo on 2006-01-25
Yeah, apparently mirrormaxed died today >_<

I'll miss mirrormax...I sure was missing it this morning when I was trying to update my machine : P

The new sources are working beautifully though, use the link provided by Adrian...just consider this a signature to that solution ^_^.

---

### Post by closeyourwindows on 2006-01-26
worked wonderfully, thanks
:D

---

### Post by ashrack on 2006-01-26
also found out today when I commented from sources.list.
why did it die?

---

### Post by AlexandreP on 2006-01-27
Looking at the sources.list from the link given by Adrian, I see the breezy-extras have been removed (and that solves the problem).  But what about the extras?  Are they going to be incorpored with the backports?

---

### Post by aysiu on 2006-01-27
[QUOTE=Sparkalo]Yeah, apparently mirrormaxed died today >_<[/QUOTE] **Today?!** As far as I know, Mirrormax died about four months ago...

---

