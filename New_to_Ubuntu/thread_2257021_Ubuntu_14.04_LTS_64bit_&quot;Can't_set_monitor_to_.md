---
title: "Ubuntu 14.04 LTS 64bit &quot;Can't set monitor to correct resolution"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by janusz979 on 2014-12-16
Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 382
CRTC 382: trying mode 640x480@73Hz with output at 1024x768@60Hz (pass 0)
CRTC 382: trying mode 640x480@73Hz with output at 1024x768@60Hz (pass 1)


Only works on 800-600 I did try all can you help me it was working before on 1024x768 but I think can do better then this please help me

---

### Post by Impavidus on 2014-12-16
This could be a graphics driver problem. Maybe you could include some information on the hardware you use (graphics card in particular). It may help if you change the thread title into something more informative, like "Can't set monitor to correct resolution". To change the title, edit your first post.

---

### Post by janusz979 on 2014-12-16
description: VGA compatible controller
       product: G72 [GeForce 7300 GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:fe7e0000-fe7fffff

---

### Post by janusz979 on 2014-12-17
System Hardware:
Processor: Intel Core 2 Quad Q9450 @ 2.67GHz (4 Cores), Motherboard: ASUS P5Q-E, Chipset: Intel 4 DRAM + ICH10R, Memory: 4096MB, Disk: 500GB Hitachi HDS72105 + 1000GB Western Digital WD10EZRX-00A, Graphics: LLVMpipe, Audio: Analog Devices AD1989B, Network: Marvell 88E8056 PCI-E Gigabit + Realtek RTL8191SEvB Wireless LAN

---

### Post by oldfred on 2014-12-17
Did you install nVidia legacy driver that is correct for your old card, or are you using nouveau?

 configuration: latency=0

You do not seem to show any video driver??

Mine shows this or nVidia if I use that.
configuration: driver=nouveau latency=0

It looks like the 304.xx is correct driver for your card.

 What is a nVidia Legacy GPU?
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
 There are presently four Legacy GPU driver series.

---

