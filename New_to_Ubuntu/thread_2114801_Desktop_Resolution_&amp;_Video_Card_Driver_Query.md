---
title: "Desktop Resolution &amp; Video Card Driver Query"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by seventhsamurai on 2013-02-11
Hi Guys

I am running Ubuntu 12.10 and everything was working fine until my Nvidia graphics card went kaput. So I had to take it out and start using the video card that is built into the motherboard which obviously isnt nearly as good. It's a 256 mb card I think.

Anyway, I'm using a Dell monitor that used to run on a nice resolution of 1440x900 when using the nice Nvidia card. Now however, I am only able to set it at a maximum of 1024x768. I do know that in windows, this built in card supports higher resolutions. Is there some driver I need to install to enable higher resolutions?

I installed Hardinfo to get the hardware specs. Here they are:

```
-Display-
Resolution        : 1024x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.13.0
-Monitors-
Monitor 0        : 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : Unknown
Renderer        : Unknown
Version        : Unknown
Direct Rendering        : No

```

```
-PCI Devices-
Host bridge        : Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
VGA compatible controller        : Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) (prog-if 00 [VGA controller])
Audio device        : Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
PCI bridge        : Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
PCI bridge        : Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
ISA bridge        : Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
IDE interface        : Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 80 [Master])
SMBus        : Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
Ethernet controller        : Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)
Host bridge        : Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
VGA compatible controller        : Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) (prog-if 00 [VGA controller])
Audio device        : Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
PCI bridge        : Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
USB controller        : Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
PCI bridge        : Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
ISA bridge        : Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
IDE interface        : Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 80 [Master])
SMBus        : Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
Ethernet controller        : Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)

```

I would appreciate your help. Thanks.

---

### Post by mastablasta on 2013-02-11
when you removed the nvidia card did you also remove the proprietary drivers from the operating system?

---

### Post by omeomi on 2013-02-11
Make sure you have removed all the nvidia-related things from your system, it should work fine then.

See this post with a comparable problem: [http://www.linuxquestions.org/questions/debian-26/intel-driver-for-82g33-g31-in-squeeze-does-not-support-3d-rendering-860838/](http://www.linuxquestions.org/questions/debian-26/intel-driver-for-82g33-g31-in-squeeze-does-not-support-3d-rendering-860838/)

---

### Post by seventhsamurai on 2013-02-11
Thank you for trying to help. During the initial installation with the Nvidia card, I never had to install any proprietary drivers. Anyway, I have solved the issue using this solution: [http://ubuntuforums.org/showthread.php?t=1022011](http://ubuntuforums.org/showthread.php?t=1022011)

Using the settings on that page, I created a new Xorg.conf file with the following settings and placed it in /etc/X11/:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"

SubSection "Display"
    Viewport    0 0
    Depth        24
    Modes        "1440x900_60.00"
EndSubSection

EndSection
```

---

