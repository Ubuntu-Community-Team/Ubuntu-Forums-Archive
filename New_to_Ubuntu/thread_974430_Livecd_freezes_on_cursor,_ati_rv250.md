---
title: "Livecd freezes on cursor, ati rv250"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by nanotube on 2008-11-07
ok, so the intrepid livecd freezes upon showing the desktop and the cursor (but before the background picture comes up).
real, hard freeze - can't ctl-alt-backspace, can't switch to a text vty, nothing.

i can boot in "safe graphics mode", i.e., using the vesa video adapter, without any problems.

i was at first suspecting that this may be a compiz problem, so i booted into safe gfx mode, uninstalled compiz (sudo apt-get remove compiz compiz-core), set the default window manager to metacity in gconf, then set the driver in xorg.conf to ati, and restarted the x server. but, no dice - it froze again (but this time right after showing the desktop background picture). 

this is happening on a dell inspiron 5150, with an ati mobility radeon 9000 video card (rv250). 

note that the machine currently runs feisty, using the foss ati driver, without any trouble. 

my testing efforts suggest that the ati driver has acquired some bug between feisty and intrepid.

some more background: i have also tested the gutsy and hardy livecds, and both fail to boot in default mode, but freeze on showing the cursor. only booting in safe graphics mode is possible.

so, i would appreciate any suggestions you may have for getting this resolved. with feisty's support period being over, i'd like to upgrade, but i need to solve this graphics problem. 

thanks!

---

### Post by mapes12 on 2008-11-07
Sorry for asking the blindingly obvious but have you tried an Alternate CD installation? My systems doesn't like the Live CD's either but Alternate's always work.

BTW - where did you get your Avatar?

---

### Post by nanotube on 2008-11-07
update: it seems that there are a few people having the same problem:
[http://ubuntuforums.org/showthread.php?t=891701&highlight=rv250+freeze](http://ubuntuforums.org/showthread.php?t=891701&highlight=rv250+freeze)
[http://ubuntuforums.org/showthread.php?t=748132&highlight=rv250+freeze](http://ubuntuforums.org/showthread.php?t=748132&highlight=rv250+freeze)

also a launchpad bug filed here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/214105](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/214105)

so... i'll try the agpmode and some other options suggested, and report back with the results...

---

### Post by nanotube on 2008-11-07
> **mapes12 said:**
> Sorry for asking the blindingly obvious but have you tried an Alternate CD installation? My systems doesn't like the Live CD's either but Alternate's always work

hi,
no i have not, but of course there's no question that the alternate cd installation will work - since the problem is with the ati driver, and the alternate cd is in text mode. the question is, what will happen /after/ installation, when i try to boot. :)

i dont want to install until i can be sure that i can get the ati driver to work. i cannot use the vesa driver, as this is on a laptop where i run dual-screen, which only ati driver will let me do. vesa doesn't even see the vga port and the attached external screen.

---

### Post by nanotube on 2008-11-08
OK, adding line
```
Option "AGPMode" "1"
```
to the xorg.conf prevents the crash. it doesn't work with agpmode 2 or 4, but at least it works with 1. :)

---

### Post by podfish on 2009-03-15
> **nanotube said:**
> OK, adding line
```
Option "AGPMode" "1"
```
to the xorg.conf prevents the crash. it doesn't work with agpmode 2 or 4, but at least it works with 1. :)

OH MY GOSH!

I have been looking for a solution to this problem for about two years.

Thank you, thank you, thank you.  I can now use my laptop again.  You are the DUDE.  It's movie time.

:popcorn:

---

### Post by nanotube on 2009-03-15
cool! :D

---

