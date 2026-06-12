---
title: "Unable to recover from Suspend on Dell Dimension 4600i"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by erisenhoover on 2012-08-11
New to Linux and Ubuntu. Long-time Mac user. Trying to learn a new skill with an old machine: Dell Dimension 4600i 2.8GHz Pentium 5. Had 512KB RAM and Windows XP SP3 on 80GB HD. 
Installed Ubuntu 12.04 on a second partition and it ran more slowly than I expected. So I tried Lubuntu 12.04. I liked it but purchased a RAM upgrade to 1GB, so tried Ubuntu again. It seemed zippy; but I am frustrated by a Suspend issue. 
If I choose Suspend from the System icon, the computer suspends. When I try to awaken it, the CPU will whir back to life, but the display only flickers momentarily then loses the signal. 
A few times I allowed the Power Management settings to put the system into Suspend after a specified timeout. Sometimes it awoke as expected. Other times it would act as above. 
Any ideas?

Hardware specs: 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P AGP Bridge (rev 02) 
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02) 
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1) 
02:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem 
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by 2F4U on 2012-08-11
Seems as if you have an nVidia card? Are you using the open source or the proprietary graphics drivers? ATI and nVidia cards with the open source drivers often require the nomodeset grub kernel parameter for suspend/resume to work correctly. Did you already try adding this parameter?

---

### Post by erisenhoover on 2012-08-11
> **2F4U said:**
> Seems as if you have an nVidia card? Are you using the open source or the proprietary graphics drivers? ATI and nVidia cards with the open source drivers often require the nomodeset grub kernel parameter for suspend/resume to work correctly. Did you already try adding this parameter?

I am afraid I don't know how to do that and certainly didn't know it was necessary. Can you help explain it to me, please?

---

### Post by ruslan kim on 2012-08-11
Hi,
I experienced the same problem and I am new to linux too. You could probably find some advices here:
[http://ubuntuforums.org/showthread.php?t=2039965](http://ubuntuforums.org/showthread.php?t=2039965)

---

### Post by erisenhoover on 2012-08-11
> **erisenhoover said:**
> I am afraid I don't know how to do that and certainly didn't know it was necessary. Can you help explain it to me, please?

Thanks to 2F4U, who got me pointed in the right direction. Google search for "how to install nvidia drivers in ubuntu" led me to

[help.ubuntu.com/community/BinaryDriverHowto/Nvidia](help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I tried System Settings > Additional Drivers but it seemed the "Nvidia accelerated graphics driver (version 173) [Recommended]" was already installed. I instead activated the "Nvidia accelerated graphics driver (post-release updates) (version 173-updates)". This didn't change the behavior. Still wouldn't recover from suspend. 
So, lower in the above page is a Suspend/Hibernation section. I followed the advice to edit [font=courier]xorg.conf[/font] and [font=courier]blacklist.conf[/font] and now I can recover from suspend.

---

### Post by d7d9d10 on 2013-02-02
I have been expirencing the same basic problem on a Dell Dimension 2400 and ubuntu 12.04 and nvidia drivers.  Selecting Suspend caused the screen to go blank and the computer to power down,  but not completely off.   The hard drives would stop but there was still a background electrical hum.    I didn't notice it at first but the LCD screen also remained on, with just a little light around the edges ( presumably the screens back lighting. )  Then I tried to wake the machine, the computer would whirl into life, but the screen would flash up the message  No VGA signal. ( I am using a vga connection)  and then shut off.  I tried not using the nvidia drivers,  but while the suspend would work the screen would be black except for a couple or line of text ( username and password or something like that.  I tried various bits of code that this forum and others suggested, but to effect.  However I now seem to have solved my problem.   I found some suggestions for changes to the BIOS  before installing Ubuntu, plus the computer only powering down in the the suspend mode lead me to make some changes in the 'power management setup' section of the BIOS.  Specifically the following  Under 'power management setup'.    ACPI suspend Type    changed from    S1     changed to   S3      PME Event lake up    changed from    enable changed to   disabled    modem ring on        changed from    enable changed to   disabled    HEPT support         changed from    enable changed to   disabled  Now on selecting suspend, the computer becomes silent and the screen goes blank and then off.  The computer did't wake in response to keyboard or mouse,  but it did wake when the power button was used.   Everthing seems to have 'come back' though it probably still took 20 seconds for everything to restored,  but it does seem to have installed a newly attacked printer at the same time.  That's as far as I far got with this,    Hope it helps you if you are having the same problem.

---

