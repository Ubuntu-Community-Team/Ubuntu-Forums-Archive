---
title: "[SOLVED] &amp;quot;Can't write page 1 header&amp;quot;"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by mancroft on 2008-11-15
Using Intrepid.

Epson D92 printer won't work.

Error: "Can't write page 1 header"

Any ideas?

---

### Post by Tea4all on 2008-11-15
Can you post the output of ```
lspci | grep epson
```? To do this go to Applications > Accessories > Terminal. Type the code into the box that shows up and press enter. Then copy the text and post here.

---

### Post by mancroft on 2008-11-15
```
john@john-desktop:~$ lspci | grep epson
```

shows nothing. But the text editor knows the printer is there.

```
john@john-desktop:~$ lspci
```

produces:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
john@john-desktop:~$
```

---

### Post by Tea4all on 2008-11-15
Try ```
lsusb | grep epson
```

---

### Post by mancroft on 2008-11-15
```
john@john-desktop:~$ lsusb | grep epson
john@john-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 09da:002b A4 Tech Co., Ltd 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-desktop:~$ 

```

Appears to show printer as Stylus D88+ but it is a D92.

---

### Post by Tea4all on 2008-11-15
That might be the problem. Your system sees the printer as an older model. Try unplugging it from the usb port, and plug it into a different one. Then try to print after it auto installs. Sometimes printer manufactures use the same chipset for more than one printer.

---

### Post by mancroft on 2008-11-15
> **Tea4all said:**
> That might be the problem. Your system sees the printer as an older model. Try unplugging it from the usb port, and plug it into a different one. Then try to print after it auto installs. Sometimes printer manufactures use the same chipset for more than one printer.

Tried that. No luck.

I unplugged the printer and restarted the computer and lsusb still thinks the printer is a Stylus D88+.

---

### Post by Tea4all on 2008-11-15
Go to system > administration > printing. Right click on the printer and choose properties. Go to make and model. Change to your printer model.

---

### Post by mancroft on 2008-11-15
Thanks. 

I solved it by going to [http://127.0.0.1:631/printers/](http://127.0.0.1:631/printers/) 

then modify printer 

and set the printer driver to: Epson Stylus D68 - CUPS+Gutenprint v5.2.0-rc1

---

### Post by Tea4all on 2008-11-16
That also works! Same thing, except it is a web interface. If the problem is solved, please close the forum.:)

---

