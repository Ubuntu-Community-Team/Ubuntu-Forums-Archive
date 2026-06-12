---
title: "Can't install timer-applet on Ubuntu 11.10"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Mojomagus on 2012-03-06
Hi,

I'm running 11.10 with Gnome classic and can't get the gnome timer applet to install.

when I try apt-get I get this message:  

The following packages have unmet dependencies:
 timer-applet : Depends: python-gnomeapplet but it is not installable
E: Unable to correct problems, you have held broken packages.

with synaptic it says to fix broken packages first.

Any ideas on this? This app has a way for me to measure my productivity/work, without it I spend too much time distracted with unimportant stuff. There doesn even seem to be a good alternative for it out there.

---

### Post by Script Warlock on 2012-03-06
can you find it in USC? according to [launchpad]("https://bugs.launchpad.net/ubuntu/+source/timer-applet/+bug/913487")

---

### Post by Mojomagus on 2012-03-06
Yeah, its in Ubuntu software centre but through there I get this error:

The following packages have unmet dependencies:

timer-applet: Depends: python (>= 2.5) but 2.7.2-7ubuntu2 is to be installed
              Depends: gconf2 (>= 2.10.1-2) but 3.2.3-0ubuntu0.1 is to be installed
              Depends: python-gtk2 (>= 2.10) but 2.24.0-2 is to be installed
              Depends: python-gnomeapplet but it is not going to be installed
              Depends: python-glade2 (>= 2.10) but 2.24.0-2 is to be installed

---

### Post by Frogs Hair on 2012-03-06
From what I can find the Timer Applet is not Gnome 3 compatible even though it appears in the software center. There was question at launch pad regarding Gnome Shell ports as an extension. The project has been taken over by a new maintainer .

---

