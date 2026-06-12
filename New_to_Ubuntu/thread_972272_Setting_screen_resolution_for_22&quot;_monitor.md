---
title: "Setting screen resolution for 22&quot; monitor"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by SomethingFishy on 2008-11-05
Hi

I have bought a new custom machine and installed Ubuntu, and I'm new to Linux.  So far so good, except I'm having trouble getting anything more than the most basic screen resolution.  Given that I spent quite a few of my English pounds on a 22" widescreen monitor, this is a little upsetting.  Please can somebody advise me?

Here's the full spec of my hardware order - I'd hate to miss anything out:

2GB DDR2 PC-5400 667 MHZ (2 x 1 GB 667)
160 GB SATA HDD UDMA 300 7200 8MB
350W PSU
Black & Silver ATX Tower Case
4 X USB 2.0 Ports
Motherboard Integrated 5.1 Sound
Fast 10/100 Ethernet Lan (Broadband Ready)
Speeze QuadroFlow VIII - Low Noise
AMD ATHLON 64 X2 5200+ 2MB SKT-AM2
Motherboard Integrated 3D Video
ASUS DVD±RW 20x DRW-2014L1T Black - LIGHTSCRIBE (SATA)
ASUS SKT-AM2 M2N-CM DVI S/V/L M-ATX 2000MT/s
ASUS LCD MONITOR 22" WIDE MW221C DVI BLACK/GUNMETAL GREY

I'm running 8.04 Hardy Heron, 64 bit.

Thanks in anticipation :)

---

### Post by Peter09 on 2008-11-05
Can you post the output of

```
lshw -C display
```

---

### Post by SomethingFishy on 2008-11-05
Thanks for the reply.  Here's what I get:

WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 7025
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0

---

### Post by Peter09 on 2008-11-05
You do not have the correct graphics card driver installed.

As a first fix try booting into recovery mode and when the menu comes up select the xfix option.

---

### Post by SomethingFishy on 2008-11-05
Thanks Peter.  That's progress - I've now got 800 x 600 instead of 640 by 480 but System menu... Screen Resolution won't give me any other options.  A click of the Detect Displays button produces no result.

---

### Post by Peter09 on 2008-11-05
What does the lshw command show now?

Also check that there is no driver asking to be enabled in System->Admin->Hardware Drivers

---

### Post by pi.boy.travis on 2008-11-05
Have you tried Ubuntu 8.10.  Ubuntu has come a long way as far as configuring X is concerned!

Go to System>Administration>Hardware Drivers, and enable the proper driver for your nVidia card.

Hope this helps!

EDIT:Peter09 posted while I was typing. . . .

---

### Post by Peter09 on 2008-11-05
Hi,
if that does not work - there is an experiment you could try.

```
sudo apt-get install nvidia-glx-177
``` 

I think that is the driver for your card (it may already be installed)

---

### Post by SomethingFishy on 2008-11-05
Thanks Peter and pi.boy.travis.  I enabled a driver in System->Admin->Hardware Drivers and after a restart I've got a whole range of resolutions to play with - fabulous!  Things are still looking a little s t r e t c h e d and the highest resolutions either lose a chunk of the desktop off the left of the screen or the menu bar heads towards heaven.  I guess it might be a question of fiddling around to find the best resolution, or is there more that I could do?

The command lshw -C display now gives:

  *-display               
       description: VGA compatible controller
       product: GeForce 7025
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by Peter09 on 2008-11-05
Great,
you may find you need to select the widescreen options in resolution to get the right aspect ratio.

---

### Post by pi.boy.travis on 2008-11-05
Perhaps a screenshot ould give some mre information?  You can take a screenshot with Applications>Accessories>Take Screenshot.

What is the maximum selectable resolution?  What is this monitor's highest possible resolution?

---

### Post by pi.boy.travis on 2008-11-05
Perhaps a screenshot could give some more information?  You can take a screenshot with Applications>Accessories>Take Screenshot.

What is the maximum selectable resolution?  What is this monitor's highest possible resolution?

EDIT: OOPS. . . double post. . . stupid wireless reception. . .

---

### Post by philinux on 2008-11-05
I've just got a 22" WS lcd the documentation says the native res is 1680x1050.

Whatever the native res is for your monitor use that.

---

### Post by SomethingFishy on 2008-11-05
Hope this isn't a daft question: should I expect to see a separate tick box for widescreen options in System>Preferences>Screen Resolution?

[Oops, just seen posts from philinux and pi.boy.travis.  I'll dig out the spec and if it doesn't help post a screenshot.  Cheers guys.]

---

### Post by philinux on 2008-11-05
I would suspect it's 1680x1050. Try it and see.

---

