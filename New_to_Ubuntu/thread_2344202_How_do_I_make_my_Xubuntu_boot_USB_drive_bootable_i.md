---
title: "How do I make my Xubuntu boot USB drive bootable in UEFI of Windows 8?"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by laggger164 on 2016-11-23
I was trying to boot up my Xubuntu USB drive on another PC... That had the horrible Windows 8...

I booted into it's boot menu and chose to boot from USB UEFI or whatever it was called. It didn't do anything, just booted up normally to Windows. Then I tried USB Legacy, same thing, nothing else looked like a viable option, but I tried them anyways. Still nothing.

I booted into the BIOS and it did see my USB drive there, but when I opened the BIOS boot menu, it wasn't there. I tried disabling Secure boot and enabling legacy. Still nothing.

It does boot up on my Windows 10 machine with the BIOS boot menu no problem. Although I don't have UEFI on it, it is from 2013 upgraded from W7 to W10.

So I gave up and posted my problem on this forum which you are now reading!

Thank you for all your replies!

---

### Post by sudodus on 2016-11-23
1. You need a Xubuntu 64-bit version. The file name contains **amd64**, and it works with Intel processors as well as with AMD processors.

2. If you ***clone*** such an iso file to a USB pendrive, for example with Xubuntu 16.04.1 amd64, it will be bootable in both BIOS mode and UEFI mode. You can clone it with the ***Ubuntu Startup Disk Creator*** or with ***mkusb*** in an Ubuntu family system (standard Ubuntu, Kubuntu, ..., Xubuntu). In Windows you can clone with ***Win32 Disk Imager***. It should also work with ***Rufus***, which I think uses another method.

3. But the most difficult thing might be to 'convince' the computer that it should boot from the USB pendrive ;-)

New computers have different and non-standard UEFI systems, that can be quite good at locking it into the installed system. If you ***tell us the computer's brand name and model***, someone who knows how to convince that kind of computer might see this thread and help you boot it.

See this link and links from it, particularly the section about UEFI.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by pugstah on 2016-11-23
Go to the BIOS settings, turn off Secure Boot, Fast Boot, check your Boot sequence and make sure USB HDD or anything similar to that should be on the top one, then enable Legacy only, and exit the BIOS settings to reboot.

---

### Post by laggger164 on 2016-11-24
> **sudodus said:**
> 1. You need a Xubuntu 64-bit version. The file name contains **amd64**, and it works with Intel processors as well as with AMD processors.

2. If you ***clone*** such an iso file to a USB pendrive, for example with Xubuntu 16.04.1 amd64, it will be bootable in both BIOS mode and UEFI mode. You can clone it with the ***Ubuntu Startup Disk Creator*** or with ***mkusb*** in an Ubuntu family system (standard Ubuntu, Kubuntu, ..., Xubuntu). In Windows you can clone with ***Win32 Disk Imager***. It should also work with ***Rufus***, which I think uses another method.

3. But the most difficult thing might be to 'convince' the computer that it should boot from the USB pendrive ;-)

New computers have different and non-standard UEFI systems, that can be quite good at locking it into the installed system. If you ***tell us the computer's brand name and model***, someone who knows how to convince that kind of computer might see this thread and help you boot it.

See this link and links from it, particularly the section about UEFI.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Alright, I just went through about a tenth of it, there's a lot to read and my head is about to explode :)

Right now I have a 64-bit Xubuntu 16.04 LTS installed (not live persistence, install). Shouldn't it boot from the boot menu of Windows then?

What are the advantages of Live persistence over Proper install? 

> **pugstah said:**
> Go to the BIOS settings, turn off Secure Boot, Fast Boot, check your Boot sequence and make sure USB HDD or anything similar to that should be on the top one, then enable Legacy only, and exit the BIOS settings to reboot.

Alright, I will try that next time. I was doing it on a public computer in a near city (don't worry, they know me there already, I regularly fix stuff for them, sometimes they let me use a PC for free), I am always careful not to disable the system completely just to run a USB drive as a test if I can use it like I want (seems like a no right now).

---

### Post by sudodus on 2016-11-24
> **laggger164 said:**
> Alright, I just went through about a tenth of it, there's a lot to read and my head is about to explode :)

Right now I have a 64-bit Xubuntu 16.04 LTS installed (not live persistence, install). Shouldn't it boot from the boot menu of Windows then?

No, Ubuntu does not boot from the Windows menu. It can install grub and boot from a grub menu, and it creates a menu entry for Windows as well. Ubuntu can also boot from the UEFI/BIOS menu of the computer, which must be activated ***before*** you arrive at the Windows menu. It is often possible with a hotkey or hotkey combination, for example Esc, F2, F9, F10, F12 (different between computers, sometimes possible to read during a couple of seconds during boot, otherwise possible to find out via the internet). You may need to set the boot order in the setup menu for the UEFI/BIOS system. See this link: [Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)
> 
What are the advantages of Live persistence over Proper install? 

Flexible and portable system. Low usage of drive space. Does not write as much to the drive (less wear of pendrives). But it cannot be updated & upgraded completely like an installed system.
> 
Alright, I will try that next time. I was doing it on a public computer in a near city (don't worry, they know me there already, I regularly fix stuff for them, sometimes they let me use a PC for free), I am always careful not to disable the system completely just to run a USB drive as a test if I can use it like I want (seems like a no right now).

Nice way to help them with the public computer and in return be able to use it :-)

---

### Post by laggger164 on 2016-11-24
> **sudodus said:**
> No, Ubuntu does not boot from the Windows menu. It can install grub and boot from a grub menu, and it creates a menu entry for Windows as well. Ubuntu can also boot from the UEFI/BIOS menu of the computer, which must be activated ***before*** you arrive at the Windows menu. It is often possible with a hotkey or hotkey combination, for example Esc, F2, F9, F10, F12 (different between computers, sometimes possible to read during a couple of seconds during boot, otherwise possible to find out via the internet). You may need to set the boot order in the setup menu for the UEFI/BIOS system. See this link: [Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

Flexible and portable system. Low usage of drive space. Does not write as much to the drive (less wear of pendrives). But it cannot be updated & upgraded completely like an installed system.


Nice way to help them with the public computer and in return be able to use it :-)

Alright, I was reading a bit more and saw that I should make a EFI system partition. I did not make that when installing the OS, I did choose the "Something else" option. Do I need that? If yes, is there any way of adding it in without wiping the drive completely? (I am thinking not)

---

### Post by sudodus on 2016-11-24
Are you sure that you need an EFI partition? If Windows 8 was installed from the manufacturer (or vendor), it is probably installed in UEFI mode, and has an EFI partition already. This partition will be used by Xubuntu too (when installed).

The Xubuntu boot drive can be cloned from a 64-bit iso file, and it will be bootable in both UEFI and BIOS mode.

So there are several things to consider. First you must be able to boot the computer from the USB pendrive.

---

### Post by yancek on 2016-11-24
You would use an EFI partition only if the current windows 8 is using EFI in which case there should already be an EFI partition for the windows files.  You need both systems using either EFI or MBR, mixing them leads to serious problems so you need to determine whether it is EFI or not first.

You need to access the BIOS and set the boot priority there and not try booting from the windows menu as pointed out above.

---

