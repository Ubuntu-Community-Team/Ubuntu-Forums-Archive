---
title: "Gateway Laptop forced to run in 2D"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by Masterangelbasher on 2013-02-27
I am very new to linux / ubuntu.  If I sound stupid, It's probably because I am.  Treat me as such. 
 I have the latest Dream Studio installed on my Gateway Laptop.  It is a Duel boot with win7 on disk 1 + D.S. on disk two.  
From the get-go I needed to use "nomodeset" to get the machine to boot.  (Laptop monitor would shut off but machine would still boot)
I am stuck in 2D Hell!!!!  it's like I'm in Windows 95 Safe Mode.  The unity Bar takes up half the screen.  Not half....but jeez....  How the hell can I get the right drivers installed.

I have updated Kernel to 3.6.9
Changed the GRUB to many different suggested settings.
gonna try shaking snake rattles and chanting in tongues over my machine soon.  Please help a feeble noob.


02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.fRULN9k9OD4
  Hardware Class: framebuffer
  Model: "Intel(r)Cantiga Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r)Cantiga Graphics Controller"
  SubVendor: "Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xc0000000-0xc3feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown.

---

### Post by MoebusNet on 2013-02-28
Since no one else has replied, I thought I might try to help. If by the 'latest Dream Studio' you mean a version based on Ubuntu 12.10 or newer, there is a possibility that your apparently older video card may not be supported:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

Look under the section for video cards. If that is indeed the case, you may have better luck with a version of Dream Studio based on Ubuntu 12.04; it seems to do a better job of supporting older video cards.

I hope this helps give you an idea of a direction to pursue; best of luck!

---

