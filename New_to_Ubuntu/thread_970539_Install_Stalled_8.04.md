---
title: "Install Stalled 8.04"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-04
During the upgrade from 7.10 to 8.04 after all the files were gathered, the install routine stopped with only a couple of files left to complete. When I reboot I get the Ubuntu Logo & the prompt for my Log On & Password. The system then continues as though it's about to read my desktop but stalls on a blank pinkish screen. Is there a way to 'kick' the system beyond this point to the desktop ?

---

### Post by mapes12 on 2008-11-04
Same happened to me after an internet based upgrade. I ended up burning an installation CD (the alternate version) and doing a fresh install from the CD. Provided that you have /home on a seperate partion to /root and make sure these are set during the "partitioning" part of the installation then all your personal settings, files, bookmarks will be perfectly preserved.

This worked for me.

---

### Post by CoCoKnots on 2008-11-04
When I re-install Ubuntu & create the separate root partition, do you mean the data files will be preserved from that point or will I be able to retrieve my orginal files intact ?

---

### Post by mapes12 on 2008-11-05
When you get to the "Partioning" stage of the installation you will be presented with some choices, one of which is "Manual". Select this then for each partition make sure you set the variables so that the installer knows where you want to place your system files i.e. /(root) and also where you have previously set your /home partition data. That way you will preserve everything and the only thing that will change is that you will have upgraded from one version of Ubuntu to another.

If you do not currently have your /home data on a seperate partion then have a look at this guide to see how to move it:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

But do this before you start the fresh installation of course.

Good luck!

---

