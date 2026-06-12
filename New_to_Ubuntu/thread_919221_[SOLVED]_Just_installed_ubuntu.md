---
title: "[SOLVED] Just installed ubuntu"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by alexham on 2008-09-13
Hi,
I have just innstalled ubuntu -8.04.1 amd64.iso. I am running Windows SP Pro SP3 on AMD Athlon 64X2 Dual Core with NVidia GeForce 6100 nForce430. and Mepis 7.0

I have no sound at all and the printer (Epson Stylus Colour 640) does not work. I suspect that these applications need to be downloaded and I would appreciate some advice as to what they are.

Many thanks,

Alex

---

### Post by Squish on 2008-09-13
Epson doesnt have a good rep for supporting linux, and its in general a lower end printer. HP would be the way to go next time you gotta buy ink (Considering that is all your usually buying, the printer is thrown in for free), its linux support is superb

anyways, you have an epson, and you need it to work, thats what is important. I would have assumed ubuntu has it installed by default, but I guess not.
[http://driverscollection.com/?file_cid=38975128335380b88a7bdd3fd3d](http://driverscollection.com/?file_cid=38975128335380b88a7bdd3fd3d)

that may be an old driver, but it is a linux driver.


As for your sound, you need to give the soundcard for us to know what to do.
edit: Oh, and welcome to ubuntu :D

---

### Post by alexham on 2008-09-14
> **Squish said:**
> Epson doesnt have a good rep for supporting linux, and its in general a lower end printer. HP would be the way to go next time you gotta buy ink (Considering that is all your usually buying, the printer is thrown in for free), its linux support is superb

anyways, you have an epson, and you need it to work, thats what is important. I would have assumed ubuntu has it installed by default, but I guess not.
[http://driverscollection.com/?file_cid=38975128335380b88a7bdd3fd3d](http://driverscollection.com/?file_cid=38975128335380b88a7bdd3fd3d)

that may be an old driver, but it is a linux driver.


As for your sound, you need to give the soundcard for us to know what to do.
edit: Oh, and welcome to ubuntu :D
Thank you Squish.  The sound card is NVidia GeForce 6100 nForce430.
I have managed to add a new printer by going into System>Preferences>Default Printer, but the sound still defeats me.

Thanks again,

Alex

---

### Post by btmiller on 2008-09-14
The Nvidia GeForce sounds liek a video card, not a sound card, although a sound card is probably built into the nForce chipset.

One thing I've noticed is that a new install the volume is often set to 0, meaning that no sound is heard. Have you tried going into alsoamixer (just type alsamixer on the command line) and cranking up the master volume? There are a couple other volume controls (PCM, surround, etc.) that you may need to adjust as well.

---

### Post by alexham on 2008-09-14
> **btmiller said:**
> The Nvidia GeForce sounds liek a video card, not a sound card, although a sound card is probably built into the nForce chipset.

One thing I've noticed is that a new install the volume is often set to 0, meaning that no sound is heard. Have you tried going into alsoamixer (just type alsamixer on the command line) and cranking up the master volume? There are a couple other volume controls (PCM, surround, etc.) that you may need to adjust as well.
Does HDA NVidia sound like a Sound Card, because that is what Alsamixer shows.  I had a look at Alsamixer in Terminal and all controls are set to "00" and no means of changing it.

More ideas?

Thanks,

Alex

---

### Post by k33bz on 2008-09-14
go to the terminal and type ```
lspci
```
and copy and paste the results here

---

### Post by alexham on 2008-09-14
> **k33bz said:**
> go to the terminal and type ```
lspci
```
and copy and paste the results here

Thank you K33bz and here it is. Alex


alex@alex-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
alex@alex-desktop:~$ @alex-desktop:~$

---

### Post by markbuntu on 2008-09-14
You can use my guide here for troubleshooting your sound problem:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

