---
title: "Ubuntu 12.10 Black Screen"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by EazyE93 on 2013-01-16
Hi,

I'm a new member here and would appreciate any help.  I've read around and can't find any issues to my specific problem.  However, if I'm wrong, please direct me to a thread where I'll find the right answer.

I recently installed Ubuntu 12.10 32 bit on an Hp pavilion dm4.  I did this on a new SSD Hard Drive because my old hard drive broke.  Therefore, it's the only OS I'm currently running.  I'm running an Intel Integrated Graphics Card.  Anyway, Ubuntu is already installed on my computer, so this isn't an issue with the actual installation like most people post about.  Upon starting up my computer, the screen always goes to black.  I've opened the grub menu and attempted a lot of the solutions that I've read online.  For more background info, I've checked if there are any additional drivers I need, which it does not list any.  I've also done some APCI debugging.  It seems the only way to get my computer running is to either add the apci=off command or pci=noapci command to the grub menu.  Adding the command apci=ht does not work, however.  I've  read this means either an issue with the ACPI table parsing code or SMS code, but everything I've read offers no solution to this

I've read that the apci controls my fan, but even when it is off, I can hear my fan  running, and my computer gets no hotter than it used to.  It seems the only information I'm missing is battery status.  Also, correct me if I'm wrong, but I believe the APCI controls IRQ routing, and my mouse will fly all around my screen every once in awhile.  Are these issues related? My real question is that I'd like a more permanent solution without having to turn the ACPI off every time I boot my computer.  Sorry for the length of my post, but I hope I've provided all the information anyone needs to help.  Thank you

---

### Post by tgalati4 on 2013-01-16
Try setting nomodeset or modeset=0 in your /etc/default/grub file then run

```
sudo update-grub
```

What may be happening is that the kernel is changing the graphics mode during boot resulting in a black screen.  By turning modeset off (nomodeset or modeset=0), it will boot and only initialize the graphics after getting to the Window Manager.

ACPI deals with power management, and that's probably not the issue here.

---

### Post by joco1500 on 2013-01-16
Your computer may not be compatible with it.
When i tried to update from 9.04 to 10.10.
didn't work.

---

### Post by EazyE93 on 2013-01-17
I've already tried setting nomodeset into the grub menu.  Both with deleting quick splash and without.  That still booted to a black screen.  The computer works perfectly if I turn acpi off, so obviously it has something to do with it

---

### Post by squakie on 2013-01-17
If you do Ctrl/salt/f1, do you get the terminal login screen?  Is so,log in and try start and see what errors show on the screen.  I've also read some threads here where a certain type of wireless adapter causes the inability to get the GUI. Also, if you can get logged in to a terminal window then post back the results of lspci so we can see both the video adapter and the wireless adapter (if there is one).

---

