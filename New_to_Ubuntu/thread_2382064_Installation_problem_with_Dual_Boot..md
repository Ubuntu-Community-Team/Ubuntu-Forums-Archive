---
title: "Installation problem with Dual Boot."
date: 2018-01-08
forum: New to Ubuntu
---

### Post by keylowgee on 2018-01-08
[http://paste.ubuntu.com/26348122/](http://paste.ubuntu.com/26348122/) is the link that I was told to past to this forum. Any help is greatly appreciated.

---

### Post by oldfred on 2018-01-08
Did you do your own Windows install to the NVMe drive? It is MBR(msdos) and then Windows is only in BIOS boot mode.
Script does not fully parse the newer NVMe drives, but it does not look like Windows is in UEFI boot mode.
And you have Ubuntu in UEFI boot mode on sdb.

UEFI and BIOS are not compatible, you may be able to dual boot only from UEFI boot menu, but may in UEFI have to turn on/off UEFI or CSM/BIOS settings to match the way you have installed systems.
Better to have all systems in same boot mode. And how you boot install media, both Windows & Ubuntu is then how it installs, UEFI or BIOS.
And if newer system, some advantages to UEFI/gpt configuration over the 35 year old, but well known BIOS/MBR configuration.

It also looks like you left Windows fast start up on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by keylowgee on 2018-01-08
I do not know if I did a windows install into my NVMe drive as I do not know what NVMe or MBR is. 

From what you are saying I have windows as BIOS and boot mode and Ubuntu in UEFI boot mode. How do I get them both into UEFI mode - with step by step guidance because I do not have technical expertise in this area. I can only boot in Ubuntu at the moment and if I try to boot in the windows partition in blank screens.

Thank you for your help.

---

### Post by oldfred on 2018-01-08
You can go into UEFI and see if you can change settings to boot in CSM/BIOS/Legacy boot mode and then choose the hard drive boot entry.
See if booting hard drive entry works without the UEFI settings changes.

If you want both systems in UEFI mode you have to totally reinstall Windows?
Did you install it yourself. If from vendor it is required to be in UEFI boot mode.
And you just have to boot Windows installer in UEFI boot mode like you did with Ubuntu installer.
Windows may complain as drive is now MBR, but you should be able to totally reinstall. But that is all Windows issues which we do not know as much about.

This is Windows 8, but Windows 10 should be very similar.
[https://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](https://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)
They suggest blank drive, so you may have to remove partitions and  convert to gpt first. You should be able to do that with Windows.
Or you can use gparted from Ubuntu live installer.

---

