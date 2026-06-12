---
title: "Compiled programs"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by Tiiba on 2005-01-25
As far as I understand, Apt doesn't see programs compiled from source. I compiled MPlayer, and then went into Synaptic and selected one of MPlayer's dependents. It tried to install its own version of Mplayer.

It would be nice to be able to manually tell the computer to ignore certain dependencies. Is there a way to do that?

---

### Post by TravisNewman on 2005-01-25
apt-get checkinstall! That program does just what you want it to do, usually. It doesn't work in every case I've thrown at it but it does work for most.

I won't go into the details on how to use it, but it's got a great man page. after you've installed it just do a 
man checkinstall

---

