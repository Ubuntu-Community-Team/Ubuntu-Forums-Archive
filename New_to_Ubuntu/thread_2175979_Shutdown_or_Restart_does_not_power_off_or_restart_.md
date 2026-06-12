---
title: "Shutdown or Restart does not power off or restart computer"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Polomint01 on 2013-09-22
Have just got a new PC with the following motherboard ASUS® H81M-C: Micro-ATX, LG1150, USB 3.0, SATA 6GBs.

I installed Ubuntu 12.04 from an install DVD, all went well.

However, when I try to shutdown/restart or logout, it goes to a black screen, and the PC is still on.

I then have to use the physical power button to switch machine off.

Not sure whats causing this, I have 12.04 on my old PC (using it now) with no problems.

I am worried that the new motherboard has some incompatibitly with 12.04?

Any help welcome.

---

### Post by davetv on 2013-09-22
For shutdown, in a terminal window try

sudo shutdown -h 0

for a restart change -h to -r

---

### Post by Polomint01 on 2013-09-22
Have now put my old HDD running ubuntu 12.04 into my PC,
Boots up fine, however same problem.

Goes to black screen when trying to shutdown/reboot or change login.

Have just noticed also, when in log in screen my wallpaper does not show(normally it does), wallpaper on desktop still their.

The new PC has UEFI boot, this may be part of the problem?

Will set up a couple of scripts for shutdown and reboot for the moment.

Any help welcome, will do some more googling.

---

