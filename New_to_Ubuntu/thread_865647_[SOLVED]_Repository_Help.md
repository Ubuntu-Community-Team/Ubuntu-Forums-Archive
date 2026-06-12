---
title: "[SOLVED] Repository Help"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-20
I am wondering what repositories you fellow ubuntu users are running in your software dources list.  Right now I have the basic ones checked and I have a repository with codecs loaded.  any others i should add?

Donald Saunders
Hershey, PA

---

### Post by scragar on 2008-07-20
been posted before, but wine ( winehq.org ) and medibuntu (medibuntu.org I think) are both common choices, but it's important to ONLY ADD SOURCES YOU TRUST.

---

### Post by ibuclaw on 2008-07-20
WINE, Kiwi, Medibuntu, Ubuntu-Tweak and Intrepid on my side :D

Here is a cat list of my sources.list.d directory
[PHP]
#Ubuntu Intrepid Alpha2
deb http://archive.ubuntu.com/ubuntu intrepid main restricted
deb http://archive.ubuntu.com/ubuntu intrepid universe multiverse
#Kiwilinux (Ubuntu 8.04 - Hardy Heron compatible)
deb http://kiwilinux.org/archive hardy main #Kiwilinux
deb-src http://kiwilinux.org/archive hardy main #Kiwilinux
## Medibuntu - Ubuntu 8.04 "Hardy Heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu
deb-src http://packages.medibuntu.org/ hardy free non-free #Medibuntu
#Ubuntu-Tweak Repository
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
[/PHP]
NOTE: If you are going to add Intrepid, **Pin Hardy**.
If you don't know what pinning is/don't understand the concepts of it after looking it up, **don't try it** ;)

Regards
Iain

---

