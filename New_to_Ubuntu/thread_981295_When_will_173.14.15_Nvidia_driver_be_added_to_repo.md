---
title: "When will 173.14.15 Nvidia driver be added to repositories"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-11-13
I would like to run the 173.14.15 nvidia driver and have been waiting for it to be added to the repositories.  Any idea when this driver may be added?

---

### Post by compiledkernel on 2008-11-13
I believe that 173.14.12 is the current release of that branch in intrepid. 

Why the interest in that specific iteration of the driver? 

Looks like in jaunty its the same.

---

### Post by igknighted on 2008-11-13
173.14.12 is the latest listed on their site (the current version in II).  I don't even see a newer version of the 173.X driver in the beta section

---

### Post by alienexplorers on 2008-11-13
In the beta drivers there is a 173.14.15 driver available which I tried to load with no success.  I am hoping envyng will update the 173 driver to the 173.14.15 driver so I can use it. The driver is listed on this page: [http://www.nvnews.net/vbulletin/showthread.php?t=122606]("http://www.nvnews.net/vbulletin/showthread.php?t=122606")

---

### Post by igknighted on 2008-11-13
What version of ubuntu are you using?

It is possible it could end up in <version>-proposed sometime, but a beta driver for legacy cards won't get rushed.  What failed about your install attempt?  It should work fine, I didn't see any requirements any recent ubuntu releases wouldn't fulfill.  Can you explain the process you used to try to install?

---

### Post by alienexplorers on 2008-11-13
I just tried to install the .run package 1 that is offered by nvidia.  I got it downloaded, but it would not run.  Hung at trying to build kernel and I thought it was something I had done.  See I have always had problems trying to get nvidia drivers to run thats why I like using envyng or jockey.
Right now I am running the 96.43.09 Beta driver and it totally messes up any KDE programs I am running unless I turn off compiz.  Thats why I was hoping that the beta 173.14.15 driver would work better.

---

### Post by igknighted on 2008-11-13
To install:

install build-essential package (sudo apt-get install build-essential), as well as kernel-headers if it doesn't bring those in too.

Stop X (sudo /etc/init.d/gdm stop) (sub kdm for gdm if you are on Kubuntu)

Run the nvidia installer (sudo sh NVIDIA_INSTALL_PACKAGE.run)

Say yes to everything, it should install fine.

Reboot.

EDIT: What nvidia card do you have?  The 5200 in your sig?  It claims it should still be supported... what issues does the default driver in ubuntu have?

---

### Post by alienexplorers on 2008-11-13
I have an old FX5200 GeForce.  Would I run package 0 or 1.  That has me confused.

---

### Post by alienexplorers on 2008-11-13
Forgot to mention that the reason I do not run the current 173.14.12 driver is due to the fact that you need a processor that runs the SSE instruction set.  The new 173.14.15 drivers dropped the need for the SSE instruction set making it compatible with my old K6-III processor.

---

