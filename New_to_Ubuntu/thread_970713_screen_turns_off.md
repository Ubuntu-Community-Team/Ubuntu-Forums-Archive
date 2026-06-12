---
title: "screen turns off"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Geir102 on 2008-11-04
Hi!

When I'am surfing the web whit firefox. The screen keeps turning off. This only happens when I'am using ubuntu. And I have to turn the power off and on on the screen to get it back. Any one know what this might be?

---

### Post by stephanvaningen on 2008-11-04
Give more info on video card/chipset. I have had that also some times with my Lenovo Thinkcentre (A61e) with ATI-card, and I think the right drivers (now with 8.10) I have not encountered it anymore...

---

### Post by Geir102 on 2008-12-30
HI, havent used this computer for a wile now so a little late sorry. I am using ubuntu 8.10 and the lates drivers i think? How do i check this. Need a little step by step

---

### Post by Geir102 on 2009-01-06
Humz no one knows? This problem is realy starting to iritate my](*,)](*,)](*,)

---

### Post by halitech on 2009-01-06
let's start with a little more info. is this a desktop (assuming yes but want to make sure) or a laptop?

open a terminal and post the output of```
lspci
```and```
lshw -C video
```

---

### Post by Geir102 on 2009-01-06
Thanks for the answer :D Yes its a desktop:)

lspci gives:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:06.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)


lshw -C video gives:
  *-display               
       description: VGA compatible controller
       product: GeForce 7100 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by halitech on 2009-01-07
hmmm, well the card is being recognized fine. are you using the restricted drivers (System - admin - restricted drivers) or the default ones or did you use envy to install them?

---

### Post by Geir102 on 2009-01-07
I'm using the restricted drivers.

---

### Post by halitech on 2009-01-07
maybe try turning them off and using the default driver, maybe something went fubar when you installed the restricted driver

---

### Post by Geir102 on 2009-01-09
I reinstalled the restricted, did not fix it :( But it seems to be fine I don't reinstall. Do this mean i cant use screen drivers at all?

---

### Post by halitech on 2009-01-09
it might be a case that there is some incompatibility between the driver and your hardware. you could try using envy to install the correct drivers and see if that works any better.

---

### Post by Geir102 on 2009-01-10
Humz seems I was a little quick in saying it was ok. The problem continues whit out the drivers. Should i still try envy?

---

### Post by lazyart on 2009-01-10
Had a similar problem with a GeForce 5200 made by PNY.  Turns out my video card had gone bad.  Do a google for leaky capacitors, look up some pictures and take a look at your video card and motherboard.

---

### Post by Dragonflyoh on 2009-01-21
Did you ever get this resolved? I have a GeForce 7100 GS and after upgrading to 8.1 I get the driver activated but not currently in use message from the hardware drivers and the failed to load the drivers at startup. I removed all Nividia files using Synaptic and then used EnvyNG to install the 96, then 173 and finally the 177 drivers and it does not work with any of them. I tried the nvidia-xconfig and that also did nothing. There were a couple other posts about the problem and nothing works. I can get back to having the screen resolution my monitor supports, 1440 x 900, but the computer is a Mythtv backend and without the driver installed I cannot access the computer from the front end machine.

---

### Post by Geir102 on 2009-01-22
I never fix it, its driving my mad. But i see the resolution is set to 1024x768 85 Hz. Recommended for this screen is 1280x1024 at 85hz. But i cant change it to that. Any one know how to fix it? Can this be it?

---

### Post by Dragonflyoh on 2009-01-22
Thanks for letting me know I am not alone in my frustration. I did get some help in setting up my system without any drivers under the following post. It may be of some help to your case. I cannot change the setup my Mythtv backend because of the video issue and will wait for a while to see if Envy or Nvidia come up with an update.

[http://ubuntuforums.org/showthread.php?t=983779](http://ubuntuforums.org/showthread.php?t=983779)

---

