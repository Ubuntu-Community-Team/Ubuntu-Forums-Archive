---
title: "Nvidia drivers ,,yet again"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by jockyburns on 2011-09-24
I'm still having a problem installing Nvidia proprietary drivers. Additional drivers shows I have the proprietary drivers installed, but not yet activated. I've been looking for a simple way to activate them , but seem to run into a brick wall of gobbledygook. 
Some have suggested opening System /Adninistration/ ???/?? (How do you do this)
Others have suggested opening a terminal and running sudo nvidia- xconfig ??.  I got this result from that;-
Using X configuration file: "/etc/X11/xorg.conf.

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'"

Dunno what this means???

Looking through the forums someone suggested running lspci -k so I did that to see which driver is being used and got this :-

v 01)
    Subsystem: ASRock Incorporation Device 27c0
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: ASRock Incorporation Device 27da
    Kernel modules: i2c-i801
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: ASRock Incorporation Device 8136
    Kernel driver in use: r8169
    Kernel modules: r8169
03:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
    Subsystem: Agere Systems Device 044c
03:02.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
    Subsystem: ASUSTeK Computer Inc. TV-FM 7134
    Kernel driver in use: saa7134
    Kernel modules: saa7134
04:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidia-173, nouveau, nvidiafb.

From what I can see , it's using the generic 173 driver and not the proprietary driver (or is this the proprietary driver???)

Anyone able to help/advise. Cheers

Running Ubuntu 11.04. 
Complete noob as far as Linux goes so answers in extremely plain English would be helpful. ;);)

---

### Post by Lisiano on 2011-09-24
Type this
```
nvidia-settings
```
Or go to System -> Administration -> NVIDIA X Server Settings
Or if you use Unity (The one with the bar and icons on the left) just search for Nvidia.

There is a bug that says you have the driver installed but not active, it actually is active.

EDIT: I forgot, if you are using Unity, you have the proprietary drivers already on.

---

### Post by Krytarik on 2011-09-24
> **Lisiano said:**
> I forgot, if you are using Unity, you have the proprietary drivers already on.
And this also indicates that ;-) (to both):
> **jockyburns said:**
> **Kernel driver in use: nvidia**
    Kernel modules: nvidia-current, nvidia-173, nouveau, nvidiafb.

> **jockyburns said:**
> From what I can see , it's using the generic 173 driver and not the proprietary driver (or is this the proprietary driver???)
Yep, both "nvidia-current" and "nvidia-173" are proprietary drivers. And both versions are installed at your system.

Do you see that in "Additional Drivers", that the "nvidia-173" is being used?

You can also run this command to check which driver is actually running:
```
/usr/lib/nux/unity_support_test -p
```Greetings.

---

