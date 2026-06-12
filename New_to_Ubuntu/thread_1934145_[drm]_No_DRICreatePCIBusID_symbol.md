---
title: "[drm] No DRICreatePCIBusID symbol"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by numala on 2012-03-01
Hi, I'm using Ubuntu 10.04. I tried to connect to a network through a ethernet wire and the computer froze. I restarted it and I could not login as, on the log-in screen, my user icon appear as a red cross. When I hit the red cross to try to log in it says "welcome to orca" and it keep refreshing the log-in screen. 

Running in console mode I tried to reinstall the X server by typing 
> sudo X :1 -configure
but it does not create the xorg.conf file. 
At the end of /var/log/Xorg.0.log I find:

> (**) module path set to "usr/lib/xorg/modules"
> (WW) allowEmptyInput is on, devices using drivers 'kbd','mouse' or 'vmmouse' will be     disabled 
> Disabling mouse 0
> Disabling keyboard0
> (EE) [drm] No DRICreatePCIBusID symbol
> Number of created screens does not match number of detected devices.
   Configuration failed

Does anybody have a clue on how could I configure the xorg to start the graphical interface?
thanks

---

### Post by gordintoronto on 2012-03-01
You could tell people about your hardware: Ethernet, video, CPU, memory. The command lspci will display some of it.

Orca is a screen reader for blind people.

You could also try a more modern version of Ubuntu.

"I could not login." What did you do, what was the result?

---

### Post by numala on 2012-03-02
Yeah, sorry...it's a dell M6500
VGA controller: nVidia corporation G92 [Quadro FX 2800M] (rev a2)
Ethernet: Broadcom Corp. NetXtreme BCM5761 e Gbit Ethernet PCIe (rev 10)
Network controller: Intel Corp. PRO/Wireless 5300 AGN [Shiloh]
CPU: intel i7, 1.87 GHz, cache 8192 kB
Video resolution 1920x1200.
8 GB RAM.
Ubuntu 10.04 64bit

I tried to boot from an Ubuntu installation CD and it boots perfectly, so I guess that I do not have hardware problems.
I tried boot-repair, that should have reinstalled GRUB, but it didn't have any effect.

When I try to log-in, I hit my name and, while I type my password it puts on a blank screen for about half a second and returns me again to the log-in screen. Actually, it does this blank screen-log in screen 3-4 times before I am able to even move the mouse on my name to try to log-in. When it stops that, it says "welcome to orca" and, then, I am able to move the mouse.

I switched to different run-levels and, at that point, I can log-in. 
I stopped GDM for all the run levels and it boots fine; at that point I log in from terminal, I start gdm by typing 
>sudo /etc/init.d/gdm start
and it puts me back to the unusable log-in screen.

As I said, when I configure xorg, it gives me these errors:
> (**) module path set to "usr/lib/xorg/modules"
> (WW) allowEmptyInput is on, devices using drivers 'kbd','mouse' or 'vmmouse' will be     disabled 
> Disabling mouse 0
> Disabling keyboard0
> (EE) [drm] No DRICreatePCIBusID symbol
> Number of created screens does not match number of detected devices.
   Configuration failed

Should I try to reinstall gdm?

---

### Post by numala on 2012-03-02
I removed and re-installed GDM without any result
(> sudo apt-get remove gdm
> sudo apt-get install gdm)
Does anybody have any idea?
Thanks

---

### Post by gordintoronto on 2012-03-02
If it were my computer, I would install Ubuntu 11.10 or Mint 12. Your computer is newer than Ubuntu 10.04, and that is more important in the Linux world than in Windows.

---

