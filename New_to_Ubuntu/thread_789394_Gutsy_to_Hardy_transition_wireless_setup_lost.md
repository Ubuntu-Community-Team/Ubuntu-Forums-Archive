---
title: "Gutsy to Hardy transition: wireless setup lost"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by LordKthulhu on 2008-05-10
Dell Latitude D600 with Broadcom BCM 4309 wireless card, Gutsy freshly installed. After much wailing and gnashing of teeth trying to set up wireless network, I found [http://ubuntuforums.org/showthread.php?t=405552](http://ubuntuforums.org/showthread.php?t=405552). Followed the instructions, worked flawlessly the first time around. Upgraded to Hardy, wireless stopped working, and attempts to follow the instructions again resulted in error messages (don't have the details, didn't occur to me to save those). Anyone had that problem before? Thanks!

---

### Post by joshsmith on 2008-05-10
you shouldnt need to do anythign complicated, simply select the driver in
system>admin>hardware drivers
your broadcom card should be listed there

but if you have done it the wrong way:

you dont need to do this bit:
# ndisc6
# ndiswrapper-common
# ndiswrapper-source
# ndiswrapper-utils-1.9 1.9

so uninstall those packages

go into synaptic package manager and check COMPLETELY remove on bcm43xx-fwcutter
this package not the way to do things on hardy (it is the old way)
restart computer
then look in system>admin>hardware drivers

---

### Post by LordKthulhu on 2008-05-10
YEEEEAH! It's working. Sweeeeet. Thanks a bunch.

---

