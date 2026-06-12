---
title: "Separate X Screens with an NVIDIA card"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Dan Solo on 2008-11-09
OK, i hope somebody can help, because i'm starting to go bald from pulling my hair out.

I don't think my request is unreasonable; I just want to play video files from my computer on the tv and before 8.10 i could easily setup an separate x screen to do so.

So i start up nvidia-settings, set the tv as a separate x screen, save to configuration file and restart. When Ubuntu boots up again my settings have been reset and the tv is set as disabled again](*,)

So, what kind of voodoo do i have to enact to get this thing working?!?!

---

### Post by Dan Solo on 2008-11-09
nevermind i fixed it myself 

used "nvidia-xconfig" to "fix" the xorg.conf file so it world play nice with nvidia-settings. then a little tweaking and it works like in the olden days

---

