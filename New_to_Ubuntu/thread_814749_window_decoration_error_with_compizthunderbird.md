---
title: "window decoration error with compiz/thunderbird"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by noorez on 2008-06-01
I am using Compiz. When I open the composing window in Thunderbird and type something into the subject, the window decorator flashes on and off each time i edit the subject. Sometimes it will even appear to scramble. This does not happen if i don't have Compiz enabled. Is there a way to fix this?

---

### Post by ajmorris on 2008-06-03
Which windows decorator are you using? Also, is it only in thunderbird?

AJ

---

### Post by noorez on 2008-06-04
this will happen when running compiz: the error will occur under both emerald and gtk window decorator. 

Similar errors seem to happen for example when I hover over the minimize,close.. buttons the window decorations will appear to flash rapidly as if it were refreshing badly...?

in Thunderbird, the decorations will simply appear and disappear as I type in the subject box.

---

### Post by ajmorris on 2008-06-04
are you using the 169.07/169.09 nvidia drivers?

---

### Post by noorez on 2008-06-04
umm.....169.12

---

### Post by PmDematagoda on 2008-06-04
What is the VGA card you use? And what Ubuntu version do you use?

---

### Post by noorez on 2008-06-04
I use and Nvidia GeForce Go 7600. Using Ubuntu 8.04

---

### Post by walkeraj on 2008-06-13
I am also experiencing this exact problem on my desktop.  It seems to be more of a problem with the way the decoration is rendered.  Sometimes, it's rendered clear or scrambled, and you see it more with this particular case because you're typing the subject and it's re-drawing it each time the window title changes.

---

### Post by moob on 2008-12-10
Hi,
this bug is discussed on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/186382") (see duplicates too).
It is problem with nvidia driver. If you don't want to wait for new one from repository you can try ["Howto fix window titlebar drawing problems with NVIDIA gfx using 180.08 beta driver"]("http://www.ubuntugeek.com/howto-fix-window-titlebar-drawing-problems-with-nvidia-gfx-using-18008-beta-driver-in-intrepid.html").

With regards.

---

