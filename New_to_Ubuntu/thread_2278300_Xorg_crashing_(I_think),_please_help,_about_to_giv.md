---
title: "Xorg crashing (I think), please help, about to give up on Linux"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by riaketty on 2015-05-15
I'm fairly new to Linux but I know the basics. I installed Mint 17 from USB, got it all running fine except one thing. I'm pretty sure it's Xorg crashing, because going into tty1 and killing Xorg fixes it, at least for a short while. But then it happens again, maybe 5 minutes or two hours later, it doesn't seem to matter. I can't figure it out and every time it happens I kind of want to smash something.

Sys Specs:
Mint 17 64 bit
Cinnamon 2.2.16
Kernel 3.13.0-24-generic
Proc AMD FX 6300
Mem 3.8GB
Gfx Nvidia GeForce GTX 660

lspci 
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller


```

See screenshot for what it's doing. I can move the mouse, click, etc. I do not get any error messages that I know of (unless it logs it somewhere?). This  has happened on both prop. Nvidia drivers and the Noveau drivers. But I'm rebooting or restarting Xorg several times a day and I lose everything when I do, which is just... frustrating as crap.

---

### Post by Lars Noodén on 2015-05-15
What about Ubuntu 14.04 LTS from USB?

---

### Post by riaketty on 2015-05-15
Worth a try, I'll d/l it. Can you turn off Unity in Ubuntu? I'm open to switching but not a big unity fan.

---

### Post by Lars Noodén on 2015-05-15
In that case you might try Xubuntu 14.04 LTS or Ubuntu MATE 14.04 LTS instead of plain Ubuntu.  The Long Term Support means that, if it works, you won't have to change your system until 2019.

---

### Post by ajgreeny on 2015-05-15
Actually, support for Xubuntu (and Lubuntu?) 14.04 is only up to 2017, I think.

However, if you are not keen on unity I would strongly recommend Xubuntu, which is fast, attractive, extremely configurable, and can be made to even look like unity with a left-hand launchbar if you want, as I use on one of my installations; see screenshot, but without some of the other annoying (to me, anyway) parts of unity.

---

### Post by riaketty on 2015-05-15
No dice. :( It happened again, the same thing, within 10 minutes of running Ubuntu. I even fully installed it to make sure it wasn't something to do with running off USB. No programs were running except Firefox and I was running an apt-get update. :( :( :(

---

### Post by riaketty on 2015-05-15
Okay so I found this
[http://ubuntuforums.org/showthread.php?t=2240996&highlight=geforce+660](http://ubuntuforums.org/showthread.php?t=2240996&highlight=geforce+660)

Running the same card. Their solution was to go to prop driver Nvidia 304. Trying that now. Do I need to get rid of Noveau completely?

---

### Post by Bashing-om on 2015-05-15
riaketty; Hello;

> **riaketty said:**
> Okay so I found this
[http://ubuntuforums.org/showthread.php?t=2240996&highlight=geforce+660](http://ubuntuforums.org/showthread.php?t=2240996&highlight=geforce+660)

Running the same card. Their solution was to go to prop driver Nvidia 304. Trying that now. Do I need to get rid of Noveau completely?

Although the installer will take care of a "nouveau" issue,  it is wise indeed to check that there is no other proprietary driver presently install and IF so remove it prior to installing the proprietary driver from "Additional Drivers" .
```

dpkg -l | grep -i nvidia

```
to verify there is none.

[INDENT][INDENT]fault isolation to resolution
[/INDENT][/INDENT]

---

### Post by riaketty on 2015-05-15
ii  libcuda1-304                                          304.125-0ubuntu0.0.1                                amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.125-0ubuntu0.0.1                                amd64        NVIDIA legacy binary driver - version 304.125
ii  nvidia-libopencl1-304                                 304.125-0ubuntu0.0.1                                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                                 304.125-0ubuntu0.0.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver



Should I be worried about that 331?
Going on an hour with no freezes. Maybe this will work.

---

### Post by Bashing-om on 2015-05-15
riaketty; Hey;

> 
Should I be worried about that 331?
bk
ii nvidia-settings 331.20-0ubuntu8 amd64 Tool for configuring the NVIDIA graphics driver

Nope, the current version of nvidia-settings is correct for your install.

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by riaketty on 2015-05-15
Thank you! Now lets see if it doesn't freak out anymore!

---

### Post by buzzingrobot on 2015-05-15
Since it has not been mentioned, the OP might consider moving to the current version of Linux Mint Cinnamon, which is 17.1.   The release notes for it include:

> [h=3]Solving freezes with some NVIDIA GeForce GPUs[/h]      If you are unable to boot Linux Mint with an NVIDIA card, or if  you are experiencing constant freezes and system lock ups, please append  "nomodeset" to your boot arguments. At the boot menu of the live  DVD/USB, press Tab to edit the boot arguments and add "nomodeset" at the  end of the line.
      If you're still having issues, you can also remove "quiet splash --" from that same line.
      Alternatively you can use the "nouveau.noaccel=1" boot argument.
      Once the system is installed, use the Driver Manager to install the nvidia-304 driver.




The schedule for 17.2 from Mint targets on end of June release.

---

