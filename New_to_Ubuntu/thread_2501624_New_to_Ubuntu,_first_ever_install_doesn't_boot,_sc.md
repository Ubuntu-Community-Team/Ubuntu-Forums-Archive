---
title: "New to Ubuntu, first ever install doesn't boot, screen pulsating"
date: 2024-10-15
forum: New to Ubuntu
---

### Post by ziggysid on 2024-10-15
Never used Ubuntu before. Seen some projects that utilise Linux so thought I'd try the desktop version and re-purpose an old laptop.
Downloaded an ISO of Ubuntu 24.04.01 LTS, then using another Windows 10 PC and RUFUS, created a boot USB Memory stick.
The old laptop is a Samsung Notebook NP300E5A with Intel i3-2330M CPU 2.2GHz
Installation appeared to go ok. Opted for a clean install (erase all and install). Opted to download 3rd party drivers.
After installation completed, rebooted but nothing happened. After the BIOS selection screen passed by, the screen went blank and then started pulsating on and off (like power to the screen/ no power to the screen).

I assumed it might be a video driver problem. Rebooted with the USB memory stick and this time opted for the Safe Graphics install. After the installation completed, the same thing happened on boot up, screen just pulsates on and off.

Tried to get into GRUB. Never used GRUB before, but I'd heard of it. I've been unable to get into GRUB, tried the Left SHFT key, tried the Esc key, doesn't start GRUB.
 
What should I try next to get this installation to bootup?

---

### Post by yancek on 2024-10-15
How old is this computer?  Did you check the hardware compatibity list for Ubuntu.

 [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

What graphics card do you have?  Use this command from a terminal on the live USB:   
lspci | grep VGA

---

### Post by ziggysid on 2024-10-15
Yes my computer meets the minimum requirements.
I can run Ubuntu from the installation USB Memory Stick, so probably not the graphics card or video driver that is the issue.

> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 130 (rev 34)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 06)



---

### Post by oldfred on 2024-10-16
Have you updated UEFI to latest available from Samsung?
Back when released there was an UEFI bug originally attributed to Linux that totally bricked system. Turned out Windows also could brick system as UEFI memory filled at 50% and caused major crash. Or UEFI issue.

You may need some UEFI/BIOS settings.
Older thread on a Samsung, issues often command across many models.
[https://ubuntuforums.org/showthread.php?t=2203824](https://ubuntuforums.org/showthread.php?t=2203824)

---

### Post by ziggysid on 2024-10-16
Oldfred, thanks for those suggestions. I read the links you provided which effectively said for Samsung DO NOT use UEFI or your computer can be bricked. And I can confirm that on my Samsung "UEFI Boot Support" is Disabled, my Samsung is not bricked.

As to updating the BIOS, I've not been able to find any BIOS updates for my NP300E5A-A01DX on the Samsung website. I can confirm its current BIOS is 09QA

---

### Post by tea for one on 2024-10-16
> **ziggysid said:**
> The old laptop is a Samsung Notebook NP300E5A with Intel i3-2330M CPU 2.2GHz
The lighter Ubuntu family members tend to work more successfully on older PCs.
I suggest that you try Lubuntu or Xubuntu.

---

### Post by ziggysid on 2024-10-18
(tea for one) Followed your suggestion and installed Lubuntu instead of Ubuntu and that is working.
Presumably, will still be able to install docker?

---

### Post by tea for one on 2024-10-18
Successful Lubuntu installation - that's good news
Open a terminal and enter:-
```
apt show docker.io
```
More info [https://www.omgubuntu.co.uk/how-to-install-docker-on-ubuntu-20-04](https://www.omgubuntu.co.uk/how-to-install-docker-on-ubuntu-20-04)

---

### Post by ziggysid on 2024-10-21
Thanks. My mistake, it was actually Docker Compose I wanted to install, that's not looking so simple. But as Lubuntu is now installed and working, I guess I ought to close this thread and start a new one.

---

