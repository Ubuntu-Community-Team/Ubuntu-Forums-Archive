---
title: "Steam installed on 15.10, not opening"
date: 2015-11-20
forum: New to Ubuntu
---

### Post by jacob93 on 2015-11-20
Feel free to move this thread to wherever you like.
Okay *Inhale* I have just dual booted my existing windows 10 with 15.10 standard and I wanted to install steam, I went to store.steampowered.com/about and downloaded the .deb
I open it and it pops open a software centre window and asks me to validate and I do. Then I try to open it and..... nothing happens. I opened it with the terminal using the steam command and it gave me this error

jacob@jacob-desktop:~$ steam
Running Steam on ubuntu 15.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast


PLEASE HELP!!!
I have no clue about Linux and I have always used windows xp even up to recently and it has *always* worked

---

### Post by mikewhatever on 2015-11-20
Do you know what graphics card model there is? You can check with the lspci command. You probably just need to install the correct driver.

---

### Post by jacob93 on 2015-11-20
here's the output of that command:

jacob@jacob-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750/8740 / R7 250E]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)

---

### Post by mikewhatever on 2015-11-20
So, it is an AMD card, and you'll need to install a proprietary AMD graphics driver for Steam to work. Unfortunately, the [latest AMD driver doesn't work on 15.10,]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Known_issues") and we've been waiting for an update since the release date of 15.10.

---

### Post by jacob93 on 2015-11-20
So, any workarounds?

---

### Post by QIII on 2015-11-20
The bug is marked as fixed, but there seems to be some confusion as to whether the appropriate package is now in the repo.

Please see the top article in my blog at theleftcoastgeek.net (link in signature).

Follow the link from there to the bug on launchpad.  I have some instructions in the bug comments for how to install from wily-proposed if the package in the normal repo does not work.

I have installed and can confirm that the new package works.

---

### Post by jacob93 on 2015-11-20
Is there any way I can downgrade to a version that works with the proper AMD driver?

This is what I get after running the update from:

[https://www.dropbox.com/sh/m3hbyrs52gb09ur/AAAjwbhtW-9Ix2pRad7YwZpca/fglrx-updates_15.201-0ubuntu1_amd64.deb?dl=0](https://www.dropbox.com/sh/m3hbyrs52gb09ur/AAAjwbhtW-9Ix2pRad7YwZpca/fglrx-updates_15.201-0ubuntu1_amd64.deb?dl=0)

jacob@jacob-desktop:~$ steam
Running Steam on ubuntu 15.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)

---

### Post by jacob93 on 2015-11-21
Thanks for the help guys, I installed 14.04 and that works a charm with everything *except* skype 4.3
Here is the link to my new topic:
[http://ubuntuforums.org/showthread.php?t=2303762](http://ubuntuforums.org/showthread.php?t=2303762)
Hope some of you guys can come help here, as well!

---

