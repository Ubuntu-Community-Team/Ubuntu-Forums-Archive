---
title: "Ubuntu 12.04 cliched laptop problems. Any GUI solutions?"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by anachronism2 on 2013-09-22
Hello to Ubuntu Forums. I'm running Ubuntu on a Toshiba Satellite and I'm encountering the regular laptop kerfuffle. First, I need a way to adjust the brightness. I've tried all the usual solutions:

"/sys/class/backlight" is a directory, but it is empty.

I added various "acpi_backlight=legacy" and such commands to the grub defaults, but nothing worked.

The ```
 xrandr --output LVDS --brightness
``` solution works, but that only controls contrast and doesn't affect power usage.

I even installed the xbrightness CLI tool, to no avail.

I am a brand-new Linux user (a week now), and I would like a simple GUI application to control brightness, power usage, and to add a sleep/hibernate mode for when I close the screen on my laptop, if anything like that exists. A CLI tool would also suffice, if one exists. I'm not ready to use Debian Linux yet, and I'd like to stick with Ubuntu if I can, but I do need to be able to adjust power use to avoid putting strain on my laptop, and my eyes. Thank you!

---

### Post by whitesmith on 2013-09-22
Brightness is not hardware-adjustable on your laptop?

---

### Post by huxley2 on 2013-09-22
I'm not sure if this answer is too simple but in 13.04 brightness and power functions can be found in System Settings. Also try downloading unity tweak tool.

---

### Post by anachronism2 on 2013-09-22
> **whitesmith said:**
> Brightness is not hardware-adjustable on your laptop?


Brightness is hardware adjustable, but I am inexperienced and I do not wish to tamper with anything critical if it can be avoided.

I have a Brightness and Lock aplication in System Settings in Unity, but the slider does not function. The application does not appear at all in the XFCE environment, and when I opened this file:

```
$ gedit '/usr/share/applications/gnome-screen-panel.desktop'
```

I noticed in the gedit file:
[I]
"OnlyShowIn=GNOME;Unity;[/I]"

This raises three questions:

1. I cannot add XFCE to this file; I do not have the neccesary permissions to change the file. Is there a sudo command to bypass that? 
2. How do I restore functionallity to the Brightness and Lock GUI, and would updating to the latest gnome-control-center stable version work (using 2.0)?

Again, I am a novice user, and this is my current understanding: The function keys and the GUI application is connected to a driver which may not be connected. I cannot so much as find this driver in /sys/class/backlight, which is an empty directory, nor do I know how to find and install the driver I need for my computer. The next step I took was to install the hardinfo package (kudos to [this thread]("http://askubuntu.com/questions/31618/how-can-i-find-my-hardware-details")) to expedite finding the information I need. Here is the summary data from the System Profile and Benchmark application:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

-Computer-
Processor        : 2x AMD E-300 APU with Radeon(tm) HD Graphics
Memory        : 3721MB (759MB used)
Operating System        : Ubuntu 12.04.3 LTS
User Name        : jjw (Anachronism)
Date/Time        : Sun 22 Sep 2013 01:34:22 PM CDT
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA ATI SB
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Toshiba input device
 ETPS/2 Elantech Touchpad
 TOSHIBA Web Camera
-Printers-
No printers found
-SCSI Disks-
ATA TOSHIBA MQ01ABD0
TSSTcorp CDDVDW SN-208AF
Generic- Multi-Card

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

And here is the PCI information:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

-PCI Devices-
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
VGA compatible controller        : Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310] (prog-if 00 [VGA controller])
SATA controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
SMBus        : Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
Audio device        : Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
ISA bridge        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
PCI bridge        : Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller        : Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
Network controller        : Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
Ethernet controller        : Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

Here is my lspci data:

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

To be honest, I can't make heads or tails out of any of that, it is mostly gibberish to me, and to understand it all I would have to research each and every piece of data, which I intend to do when I have the time. What catches my eye, at a glance, is that the openGL renderer is unknown. A quick search [indicates ]("http://www.opengl.org/discussion_boards/showthread.php/145702-Brightness-Contrast")that OpenGL drivers have a pronounced effect on rendering, contrast, and brightness. Further research from [stackexchange.com ]("http://unix.stackexchange.com/questions/27918/getting-opengl-to-work-under-ubuntu") seems to show that solutions to the problem exist. A Google search of openGL renderer unknown AND brightness problems returns [this]("http://forums.debian.net/viewtopic.php?f=7&t=104779") page. I cannot find any information on the "grep -i bug" command with a quick search, and the "glxinfo | grep render" command requires installation of mesa-utils, which leads me down a rabbit-hole, and it would be unwise to pursue solutions here since it's for a different OS. Back to the Google results, I cannot find anything specific to Ubuntu 12.04, so I choose to cease this line of research.

Next, I researched solutions to the Brightness and Lock application. I found[ this]("http://askubuntu.com/questions/293925/brightness-buttons-not-working-properly") page, with a new alternative. I changed the grub file to: "quiet splash" "acpi_osi=/"!Windows2012/" acpi_backlight=vendor" to see what would happen. It gave me back an error, that /!Windows2012/ could not be found, so I changed it back to acpi_osi=Linux. This is my current progress. I'll reboot now and report back.

---

### Post by anachronism2 on 2013-09-22
Testing... Nada. FN + F6 or F7 is moot. No brightness box, no adjustments. Next attempt, I'll change to acpi_backlight=legacy

---

### Post by Toz on 2013-09-22
> **anachronism2 said:**
> Testing... Nada. FN + F6 or F7 is moot. No brightness box, no adjustments. Next attempt, I'll change to acpi_backlight=legacy

I would give "acpi_backlight=vendor" a try instead. On reboot, can you post back:
1. You current kernel boot line:
```
cat /proc/cmdline
```
2. Your backlight interfaces and current settings:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by anachronism2 on 2013-09-22
Okay, now I have a brightness box with the function keys, but the keys and slider still do nothing. I will narrow down my research to my precise computer and OS and report.

---

### Post by Toz on 2013-09-22
>  I changed the grub file to: "quiet splash" "acpi_osi=/"!Windows2012/" acpi_backlight=vendor" to see what would happen. It gave me back an error, that /!Windows2012/ could not be found, so I changed it back to acpi_osi=Linux. 
Its a little tricky to get right. The GRUB_CMDLINE_LINUX_DEFAULT line should read:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```
...you can try skipping the acpi_backlight=vendor parameter here.

---

### Post by anachronism2 on 2013-09-22
> **Toz said:**
> I would give "acpi_backlight=vendor" a try instead. On reboot, can you post back:
1. You current kernel boot line:
```
cat /proc/cmdline
```
2. Your backlight interfaces and current settings:
**```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```**
Output:

```
/sys/class/backlight/acpi_video0
5
5
7
```

Could you please explain what this output means?

---

### Post by anachronism2 on 2013-09-22
Sorry, that post went ary. Here is my kernel boot line:

```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=6acc3e1f-d258-4842-8dad-a2a81d61a824 ro quiet splash acpi_osi=Linux acpi_backlight=legacy vt.handoff=7
```

---

### Post by Toz on 2013-09-22
You have one backlight interface - **acpi_video0**. This is good.
The current and actual brightness values are 5. 
The maimum brightness value for this interface is 7.

You can manually manipulate the backlight using a command like:
```
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

Have you tried the **acpi_backlight=vendor** parameter yet? It might yield different results in your backlight interfaces.

---

### Post by anachronism2 on 2013-09-22
None of those echo commands functioned. They returned the values but did not visibly affect my screen. You did introduce me to the **tee** command, however. Thank you.

Rebooting now with **acpi_backlight=vendor**

---

### Post by anachronism2 on 2013-09-22
**=vendor** just serves to disable both the brightness window (from function keys) and the brightness slider in the GUI. **=legacy** restores these things, but does not give them functionality. It's like if the throttle on my motorcycle would twist but not give power to the engine. Except, this problem doesn't cause my OS to crash... I am able to adjust contrast with

```
xrandr --output LVDS --brightness(X)
```

and I will set that as an alias as soon as I figure out how to.

---

### Post by Toz on 2013-09-22
Interesting. Have you installed the proprietary ATI video driver? Or are you running the opensource one?
```
lspci -k | grep -A3 VGA
```
...radeon=opensource, fglrx=proprietary.

---

### Post by anachronism2 on 2013-09-22
> **Toz said:**
> Interesting. Have you installed the proprietary ATI video driver? Or are you running the opensource one?
```
lspci -k | grep -A3 VGA
```
...radeon=opensource, fglrx=proprietary.

That was enlightening, thank you Toz.

```
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6310]
    Subsystem: Toshiba America Info Systems Device fde8
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_experimental_13, radeon

```

Hmm... it looks like I'm using the proprietory driver but it's compatible with Radeon graphics. Is that right? I'm going to search for how to change the driver in case I need to.

What does **fglrx_experimental_13,radeon** mean by experimental? Is that an alpha or beta driver, perhaps?

---

### Post by Toz on 2013-09-22
> What does fglrx_experimental_13,radeon mean by experimental? Is that an alpha or beta driver, perhaps? 
Unfortunately, I don't have any experience with ATI drivers. However, I would guess that it is an beta driver of some sort.

---

### Post by squakie on 2013-09-22
I also am curious if you don't just have a function key combo that adjusts the brightness.  Usually it's as simple as holding down the FN key and pressing a key that shows a brightness up symbol.

Nothing difficult there - just try it first.  If it doesn't work, then contiune on with the other help.

---

### Post by anachronism2 on 2013-09-25
I installed the latest ATI/AMD proprietary FGLRX graphics driver, and I also tried the beta version. Function keys and brightness slider still appear, but are still not working. Using **Toshiba Satellite C655D-S5511**. **Kernel version 3.8.0-31 **. The kernel version is listed on [launchpad]("https://launchpad.net/ubuntu/precise/i386/linux-image-3.8.0-30-generic") but not on the official [website]("https://www.kernel.org/"), I do not know why. After I download, configure, and make install the latest stable version 3.11.1, I will report back.

This [search]("https://www.google.com/search?client=ubuntu&channel=fs&q=Toshiba+Satellite+C655D-S5511+ubuntu+12.04+kernel+3.8+problems&ie=utf-8&oe=utf-8#channel=fs&psj=1&q=Toshiba+Satellite+C655D-S5511+ubuntu+12.04+kernel+3.8&safe=off") is null, for my specific computer, OS version, and Kernel version.

This [search]("https://www.google.com/search?client=ubuntu&channel=fs&q=Toshiba+Satellite+C655D-S5511+ubuntu+12.04+kernel+3.8+problems&ie=utf-8&oe=utf-8#channel=fs&psj=1&q=Toshiba+Satellite+C655D-S5511+ubuntu+12.04+problems&safe=off") returns five results, for my specific computer and OS version.

---

### Post by Toz on 2013-09-25
> **anachronism2 said:**
> I installed the latest ATI/AMD proprietary FGLRX graphics driver, and I also tried the beta version. Function keys and brightness slider still appear, but are still not working.
Do you still have the same backlight interfaces?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by anachronism2 on 2013-09-25
> **Toz said:**
> Do you still have the same backlight interfaces?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Yes, 

```
/sys/class/backlight/acpi_video0
7
7
7
```

---

### Post by anachronism2 on 2013-09-25
I am now using Linux kernel 3.11.1-31 generic. No change. Should I try anything further, or list this under incompatible laptops?

---

### Post by Toz on 2013-09-26
> **anachronism2 said:**
> I am now using Linux kernel 3.11.1-31 generic. No change. Should I try anything further, or list this under incompatible laptops?
I think it may be best to create a bug report for this issue. Do you have a setting somewhere in the Catalyst Control Centre that allows you to manually change the brightness?

---

### Post by anachronism2 on 2013-09-26
> **Toz said:**
> I think it may be best to create a bug report for this issue. Do you have a setting somewhere in the Catalyst Control Centre that allows you to manually change the brightness?

It's going to be a while. I reinstalled Windows and just killed the grub, and I'll have to find somewhere to download the huge Linux-secure-remix iso to repair the issue. If only it was on BitTorrent.

---

### Post by anachronism2 on 2013-09-27
Okay, the Catalyst Control Center does not have a setting for brightness control. I tried Ubuntu 10.04 Lucid on live CD, as well as 13.04 Raring on the secure-remix live CD, and brightness controls worked in 10.04, both function keys and brightness slider. Did not work in 13.04. What factors does this elliminate and indicate?

---

### Post by Toz on 2013-09-27
Different kernel versions, different Xorg versions and different catalyst driver versions.

Did you reinstall? If so, can you post back the new:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
```
pastebinit /var/log/dmesg
```
```
pastebinit /var/log/Xorg.0.log
```

---

### Post by anachronism2 on 2013-09-28
> **Toz said:**
> Different kernel versions, different Xorg versions and different catalyst driver versions.

Did you reinstall? If so, can you post back the new:
```
cat /proc/cmdline
```

```
jjw@jjw-Satellite-C655D:~$ cat  /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.1-031101-generic root=UUID=6acc3e1f-d258-4842-8dad-a2a81d61a824 ro quiet splash acpi_osi=Linux acpi_backlight=legacy vt.handoff=7
```

The legacy acpi displays the brightness slider and function keys brightness window, but does not affect brightness. The vendor acpi does not display either and does not affect brightness.

> ```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

```
jjw@jjw-Satellite-C655D:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
7
7
7

```


> ```
pastebinit /var/log/dmesg
```[quote]

Fascinating, pastebinit. Here's your link: [http://paste.ubuntu.com/6167612/](http://paste.ubuntu.com/6167612/)

[quote]```
pastebinit /var/log/Xorg.0.log
```

Second link:[URL="http://paste.ubuntu.com/6167667/"] [http://paste.ubuntu.com/6167667/](http://paste.ubuntu.com/6167667/)
[/URL]

---

### Post by anachronism2 on 2013-09-28
This is interesting, from the /var/log/dmesg paste:

```

[    0.238038] ACPI: Executed 1 blocks of module-level executable AML code
[    0.244397] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.290199] ACPI: Interpreter enabled
[    0.290224] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.290235] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.290271] ACPI: (supports S0 S3 S4 S5)
[    0.290276] ACPI: Using IOAPIC for interrupt routing
[    0.290658] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.290939] ACPI: No dock devices found.
[    0.323834] ACPI: Power Resource [PFA1] (off)
[    0.324550] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.324901] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce1ff])
[    0.324914] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
```

---

### Post by Toz on 2013-09-28
> **anachronism2 said:**
> This is interesting, from the /var/log/dmesg paste:

```

[    0.238038] ACPI: Executed 1 blocks of module-level executable AML code
[    0.244397] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.290199] ACPI: Interpreter enabled
[    0.290224] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.290235] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.290271] ACPI: (supports S0 S3 S4 S5)
[    0.290276] ACPI: Using IOAPIC for interrupt routing
[    0.290658] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.290939] ACPI: No dock devices found.
[    0.323834] ACPI: Power Resource [PFA1] (off)
[    0.324550] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.324901] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce1ff])
[    0.324914] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
```

Everything looks good here
> [    0.244397] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
...don't know why they say bug here, it simply means that you specified the OS on the command line (acpi_osi=Linux) and its not going to go find out which one it is.
> [    0.290224] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.290235] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.290271] ACPI: (supports S0 S3 S4 S5)
...the computer only supports the listed sleep states.
> [    0.324901] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce1ff])
[    0.324914] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
...I don't think this will affect the brightness.

I find it interesting the acpi_backlight=legacy gives you a backlight interface and only one backlight interface, but it can't be manipulated. What kernel modules are loaded?
```
lsmod
```

Can you now manually adjust brightness via:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

From your Xorg log file:
> [    16.659] (EE) fglrx(0): atiddxDriScreenInit failed. Probably kernel module missing or incompatible. 
[    16.659] (WW) fglrx(0): ***********************************************************
[    16.659] (WW) fglrx(0): * DRI initialization failed                               *
[    16.659] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    16.659] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    16.659] (WW) fglrx(0): ***********************************************************
...I don't think this would affect brightness control, but you should probably look into this if you're expecting 2D/3D acceleration.

---

### Post by anachronism2 on 2013-09-28
> **Toz said:**
> 

I find it interesting the acpi_backlight=legacy gives you a backlight interface and only one backlight interface, but it can't be manipulated. What kernel modules are loaded?
```
lsmod
```

```

jjw@jjw-Satellite-C655D:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            48631  1 
rfcomm                 58965  4 
bnep                   19143  2 
bluetooth             337841  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  17423  0 
arc4                   12509  2 
snd_hda_codec_conexant    47414  1 
joydev                 17329  0 
snd_hda_intel          43326  3 
snd_hda_codec         169534  2 snd_hda_codec_conexant,snd_hda_intel
rtl8192ce              53627  0 
rtl8192c_common        47891  1 rtl8192ce
rtl_pci                26727  1 rtl8192ce
rtlwifi                53299  2 rtl8192ce,rtl_pci
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
mac80211              534726  3 rtl8192ce,rtl_pci,rtlwifi
snd_rawmidi            25157  1 snd_seq_midi
sp5100_tco             13754  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              415946  2 rtlwifi,mac80211
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              17843  0 
snd                    61270  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                92648  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
shpchp                 32265  0 
toshiba_acpi           18382  0 
sparse_keymap          13658  1 toshiba_acpi
k10temp                12997  0 
video                  19046  0 
serio_raw              13189  0 
mac_hid                13077  0 
wmi                    18744  1 toshiba_acpi
ohci_pci               13305  0 
lp                     13359  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   25703  2 
atl1c                  41595  0 
libahci                30834  1 ahci

```


> Can you now manually adjust brightness via:
```
echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

[code=jjw@jjw-Satellite-C655D:~$ echo 4 | sudo tee /sys/class/backlight/acpi_video0/brightness0.8
4[/code]

No brightness change.

I'll respond to the Xorg code next post, I don't know why this multipost isn't working.

---

### Post by anachronism2 on 2013-09-28
> From your Xorg log file:
 	 		 			 			 				```

[    16.659] (EE) fglrx(0): atiddxDriScreenInit failed. Probably kernel module missing or incompatible. 
[    16.659] (WW) fglrx(0): **************************************************  *********
[    16.659] (WW) fglrx(0): * DRI initialization failed                               *
[    16.659] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    16.659] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    16.659] (WW) fglrx(0): **************************************************  ********* 			 		

```

 	
 
...I don't think this would affect brightness control, but you  should probably look into this if you're expecting 2D/3D acceleration.

My AMD drivers refuse to activate. I have the latest stable version and the beta version, I have tried using the Additional Drivers program to activate one, yet after restart neither one will activate.

---

### Post by Toz on 2013-09-28
Lets have a closer look at the **toshiba_acpi** kernel module.

First, according to [http://memebeam.org/toys/ToshibaAcpiDriver]("http://memebeam.org/toys/ToshibaAcpiDriver"), does a **/proc/acpi/toshiba/lcd** file exist, and if so:
```
cat /proc/acpi/toshiba/lcd
```
...and
```
echo "brightness:4" | sudo tee /proc/acpi/toshiba/lcd
```
...does it change brightness?

Secondly, can you unload it:
```
sudo modprobe -r toshiba_acpi
```
...and does it make a difference with brightness control using the function keys and slider?

---

### Post by anachronism2 on 2013-09-29
> **Toz said:**
> Lets have a closer look at the **toshiba_acpi** kernel module.

First, according to [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver), does a **/proc/acpi/toshiba/lcd** file exist, and if so:
```
cat /proc/acpi/toshiba/lcd
```

I'm afraid not. 

```
jjw@jjw-Satellite-C655D:~$ uname -sr
Linux 3.11.1-031101-generic
jjw@jjw-Satellite-C655D:~$ ls /proc/acpi
button    event  toshiba    wakeup
jjw@jjw-Satellite-C655D:~$ ls /proc/acpi/toshiba
keys  version
jjw@jjw-Satellite-C655D:~$ cat /proc/acpi/toshiba/version
driver:                  0.19
proc_interface:          1
jjw@jjw-Satellite-C655D:~$ cat /proc/acpi/toshiba/keys
hotkey_ready:            0
hotkey:                  0x0000

```

Well. I may be a n00b, but that looks glum. Now, what would happen if I downgraded my Linux kernel? As I said, brightness works fine in Ubuntu 10.04 using the default kernel. Also, as a side note, I'm currently using the XFCE 4.8 desktop enviro and, while it has the brightness box, it does not have the Brightness and Lock application, only Unity and GNOME does.
> 

...and
```
echo "brightness:4" | sudo tee /proc/acpi/toshiba/lcd
```
...does it change brightnes

Secondly, can you unload it:
```
sudo modprobe -r toshiba_acpi
```
...and does it make a difference with brightness control using the function keys and slider?

I trust you because you are a forum moderator, but I don't see an option on the manpage to reload modules...

```
jjw@jjw-Satellite-C655D:~$ sudo modprobe -r toshiba_acpi
[sudo] password for jjw: 
jjw@jjw-Satellite-C655D:~$ 
```

No change. I am still intrigued by the disabillity of the drivers. I'm going to research why they just won't activate. If I can't find any leads, I'll purge the beta driver and see what happens--I'd have a bug report in that case. I ran the Additonal Drivers application with each driver, rebooted, and found both of them inactive.

#P.S. I apologize if you are offended by the post delay. I'm moving soon, and I have bills to shuffle and things to sell and etc etc etc.

---

### Post by Toz on 2013-09-29
> **anachronism2 said:**
> #P.S. I apologize if you are offended by the post delay. I'm moving soon, and I have bills to shuffle and things to sell and etc etc etc.
No apologies required.

>  Also, as a side note, I'm currently using the XFCE 4.8 desktop enviro and, while it has the brightness box, it does not have the Brightness and Lock application, only Unity and GNOME does.
Actually, there is one. You have to install the **xfce4-power-manager-plugins** package and then add it to the panel.

---

### Post by anachronism2 on 2013-09-29
> **Toz said:**
> No apologies required.


Actually, there is one. You have to install the **xfce4-power-manager-plugins** package and then add it to the panel.

Duly noted. Thank you.

Now then, as Thomas Edison would have said, "I didn't fail a hundred times, I just found a hundred ways not to enable ACPI support on a Toshiba C655D Laptop running Linux."

```
jjw@jjw-Satellite-C655D:~$ sudo apt-get install fnfxd
[sudo] password for jjw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fnfx-client
The following NEW packages will be installed:
  fnfxd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.4 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe fnfxd i386 0.3-14ubuntu1 [20.4 kB]
Fetched 20.4 kB in 5s (3,423 B/s)
Selecting previously unselected package fnfxd.
(Reading database ... 308366 files and directories currently installed.)
Unpacking fnfxd (from .../fnfxd_0.3-14ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fnfxd (0.3-14ubuntu1) ...
Starting Toshiba hotkeys utils: FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/lcd.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

invoke-rc.d: initscript fnfxd, action "start" failed.
jjw@jjw-Satellite-C655D:~$ 

```

Blast it. Let's see what happens when I install the client package first.

```
jjw@jjw-Satellite-C655D:~$ sudo apt-get install fnfx-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fnfx-client
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,656 B of archives.
After this operation, 53.2 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe fnfx-client i386 0.3-14ubuntu1 [7,656 B]
Fetched 7,656 B in 1s (4,167 B/s)
Selecting previously unselected package fnfx-client.
(Reading database ... 308379 files and directories currently installed.)
Unpacking fnfx-client (from .../fnfx-client_0.3-14ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up fnfx-client (0.3-14ubuntu1) ...
jjw@jjw-Satellite-C655D:~$ sudo apt-get install fnfxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fnfxd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jjw@jjw-Satellite-C655D:~$ 

```

This is really fascinating, I love a challenge. I wonder what the solution to this will be.

There is also the Xbrightness program. I downloaded it, but I can't install it. Just look at these really weird dependent libraries:

```
 DEPLIBS = $(DEPXXF86VMLIB) XawClientDepLibs
  SYS_LIBRARIES = MathLibrary
LOCAL_LIBRARIES = $(XXF86VMLIB) XawClientLibs
           SRCS = xbrightness.c
           OBJS = xbrightness.o

ComplexProgramTarget(xbrightness)
```

I couldn't find the first or third one on Launchpad, or anywhere else.

It still seems like the driver itself is dysfunctional, and for some reason, I get different results depending on the enviro. XFCE4 pretends to activate the driver and prompts me to reboot, but does not activate the driver on reboot. Unity gives me an error message and logfile--or, it did the first time. I repeated my action and got different results: the Aditional Drivers app loaded, flashed, and crashed. Sent crash report. On load three and after reboot, it is now working, but as of right now the download is hanging for no apparent reason. I'll report if it ever finishes.

Here is a link to the [jockey.log.1]("http://paste.ubuntu.com/6173869/") file. It's friggin' HUGE. Lots and lots and lots and lots of missing modules and no Xorg driver set, apparently. I don't know, maybe Toshiba Co harbors a grudge against Unix-based systems.

---

### Post by Toz on 2013-09-30
Do you get these same issues (post #34) when you boot with the stock kernel that comes with the distro you've installed (12.04, right?, or 13.04?). 

Maybe you can try grabbing the 13.10 live cd and booting with it to see if you get further.

---

