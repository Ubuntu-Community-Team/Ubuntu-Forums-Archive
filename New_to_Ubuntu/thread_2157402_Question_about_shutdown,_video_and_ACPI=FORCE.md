---
title: "Question about shutdown, video and ACPI=FORCE"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by CrankyOldMan on 2013-06-25
Hi!  I installed 12.04LTS on my desktop not too long ago, and have been having several problems.  

First thing I noticed is the machine never turns off.  The shutdown appears to be going fine, then stalls after a few sweeps through the "red dots".  From there, I've been forcing the shutdown by mashing the power button on the machine.  Works, but annoying.  I should note that this machine is dual boot (Windows XP), and XP shuts the machine down just fine.

Other problem is the video mode for the Ubuntu desktop.  (I forget what it is called.)   It defaults to 2D mode.  It won't boot if I try to use the 3D mode.   The installation picked the default driver.  Whenever I install another driver it puts me in a reduce resolution mode that prevents me from reaching any buttons.

Yesterday someone suggested I put ACPI=FORCE in the Grub boot menu.  It fixed the shutdown.  However the launcher menus are all compressed and distorted at the bottom.

The motherboard is a Gigabyte GA-EP45-UD3P, and the video card is a EGA GT9800-512.

---

### Post by dino99 on 2013-06-25
GT9800: so it handle 3D
note that 13.04 is way better than that LTS
purge all the installed graphic drivers, then install nvidia-313-updates (and xserver-xorg-video-nouveau)
be sure there is no xorg.conf then reboot

---

### Post by CrankyOldMan on 2013-06-26
Sir:
Thank you for your reply.  Are you saying I can't do this in 12.04LTS, and that I should upgrade before making the changes?   Or can I do this stuff from 12.04LTS?   Far as I know, the only video driver installed now, is the default driver. But HOW would I make sure any other video drivers are purged?   And how do I go about doing the installs?  I am not an experienced user.

---

