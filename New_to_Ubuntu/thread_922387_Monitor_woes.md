---
title: "Monitor woes"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by stans on 2008-09-17
I'm being challenged by my KDS XF-7s monitor resolution setting; it's too low.

After spending a few hours reviewing dozens of posts and references to how-to articles and experimenting with xorg.conf it is time to ask for assistance because nothing is working. 

I'm working with an old clone (just installed 8.04 yesterday) that has an unknown video card in it. DDCPROBE doesn't provide vendor/product info but does tell me 'SiS' is the OEM.

I have run gksu displayconfig-gtk and the newer replacement for it on the recovery boot screen. 

Any assistance would be greatly appreciated at this point...

---

### Post by LowSky on 2008-09-17
in terminal type ```
lspci
``` and post the info here, it should list the video card

---

### Post by stans on 2008-09-17
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:07.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by LowSky on 2008-09-17
in terminal type
```
gksu gedit /etc/X11/xorg.conf

```
Replace Driver "sis" with Driver "vesa" in Section Device 'Video Card" of xorg.conf file, then restart the machine.

if worse come to worse you can reset xorg with booting into Recovery mode from grub.

What resolution are you trying to use?

---

### Post by stans on 2008-09-17
Thanks for your assistance.

I've reverted back to the basic conf file - so may need to add more lines. trying to use 1024 x 768... according to Officedepot specs the max for that model is 1280 x 1024.

---

### Post by alienexplorers on 2008-09-17
You might be able to add a modeline to your monitor section of your xorg.conf file.  I have an example listed here:
> terminator@terminator-desktop:~$ gtf 1024 768 85

  # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync



To generate one of a different resolution and refresh rate use:
> gtf horz vert refresh

---

### Post by stans on 2008-09-17
The modeline by itself doesn't work as there must be a bunch of other stuff required. I'm in low res mode now.

Is there any detection software that works ? I've tried xfix, dpkg-reconfigure, gksu...

---

### Post by alienexplorers on 2008-09-17
Yes the mode line requires horz sync, vert refresh, and a mode line in screen section of xorg.conf....

---

### Post by stans on 2008-09-18
I've got the resolution correct now - and thanks to all that provided input.

---

