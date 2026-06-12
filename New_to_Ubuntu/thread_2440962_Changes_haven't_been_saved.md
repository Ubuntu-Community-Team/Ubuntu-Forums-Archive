---
title: "Changes haven't been saved"
date: 2020-04-17
forum: New to Ubuntu
---

### Post by tbarhaim on 2020-04-17
Hello,

Replaced my former OS to ubuntu today.

I have made some changes and download some stuff, but when i rebooted my PC and got back, nothing was saved. not my users and none of the files that I have downloaded and updated.

what would be the reason? how can i retrieve my actions or save them for next time?

TIA

---

### Post by yancek on 2020-04-17
Did you download and install Ubuntu to your hard drive?  The behavior you are reporting is expected if you simply downloaded Ubuntu and wrote it to a DVD or USB and used it in that manner.

---

### Post by tbarhaim on 2020-04-17
I think I did, but not sure. used Virtualbox to switch from Windows.

Also, i have been trying to configure my root user but facing troubles with this aswell.. might be the reason?

---

### Post by CelticWarrior on 2020-04-17
So many wrong things to unpack here I'm not sure I can handle it all :mrgreen:

>                      I think I did, but not sure. used Virtualbox to switch from Windows.
Well, don't you think you need to know what you're doing, at least the very basic stuff?
Virtualbox implies running a guest OS inside another, the host OS. But in the first post you said >  Replaced my former OS to ubuntu today Now I'm confused and so is anybody else. What are you trying to do exactly? Using Ubuntu in a virtual machine is not the same as installing it.

> Also, i have been trying to configure my root user but facing troubles with this aswell.. might be the reason?
No. Two things:
[LIST=1]
[*]You don't need and shouldn't "configure root user". In Ubuntu the root account is disabled by default, we use "sudo" to obtain root rights for operations that need them and absolutely nothing else. 
[*]However, #1 isn't the reason for whatever predicament you're in - absolutely not clear yet -, the reason is it seems you don't know what you're doing and/or aren't explaining yourself properly. So, please describe in a succinct and assertive way a) what you're trying to do, your end goal, and b) what steps you took towards that goal. 
[/LIST]

---

### Post by tbarhaim on 2020-04-18
You are right. I'm quite lost to be honest. 

I just wanted to try out the Linux OS and been stuck here since, so i'll try to focus my current struggles and describe the facts:

1. I used VM to move from WIN10 (Host) to Ubuntu 18.04. After installation of Ubuntu, I rebooted my PC and can't figure out how to return to Windows (been trying to read manuals @google but can't actually succeed doing anything). Don't know if maybe by accident i overridden my Windows. Would be nice if you could explain how can I try to return to Windows.

2. After installation of Ubuntu, i downloaded stuff and organized my desktop, however when i rebooted, nothing was saved (including users I opened).

3. I'm facing multiple bugs here in Ubuntu, which includes no sound and having real trouble downloading basic stuff like chrome and flash because I don't know how to access my root user. Can you please refer me to any good beginner's manual about managing stuff here?

Thank you for your time!

---

### Post by dino99 on 2020-04-18
If you google around 'win10 vm ubuntu' you will get lot of threads like:  [https://askubuntu.com/questions/1121951/better-vm-ubuntu-on-windows-10-or-vm-windows-10-on-ubuntu](https://askubuntu.com/questions/1121951/better-vm-ubuntu-on-windows-10-or-vm-windows-10-on-ubuntu)

---

### Post by CelticWarrior on 2020-04-18
> **tbarhaim said:**
> 1. I used VM to move from WIN10 (Host) to Ubuntu 18.04. After installation of Ubuntu, I rebooted my PC and can't figure out how to return to Windows (been trying to read manuals @google but can't actually succeed doing anything). Don't know if maybe by accident i overridden my Windows. Would be nice if you could explain how can I try to return to Windows.

You need to explain with more detail what you actually did.
Typically a VM (Virtual Machine) is managed by some virtualization software - Oracle Virtualbox, VMWare, etc. - which is a program like any other installed in the OS (host). Then, within that software, we can configure VMs and use the same installer as we would use if installing directly in the real machine, but in a contained virtual hardware environment. So, from the host OS point-of-view our VMs are just files.

If you actually did what I just described nothing would have happened to the Windows bootloader and Windows would boot normally as always, because all that would have been done is the installation of software like any other. This is the crux of the huge confusion that seems to going on. I (we all actually) am having an hard time understanding what really happened. If I were to guess I would say this has nothing to do with virtual machines, you actually booted the Ubuntu installer and actually installed Ubuntu and yes, you may have overwritten Windows.

Always best to see details. I hope you'll be able to follow this instructions but not sure: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . Please boot an Ubuntu live session and follow the instructions for the 2nd option (don't try the 1st because that ISO is hopelessly outdated). DO NOT CLICK "RECOMMENDED REPAIR" or anything else other than "CREATE A BOOTINFO SUMMARY". This will generate a report that we can analyze to understand what the situation is.

>  2. After installation of Ubuntu, i downloaded stuff and organized my  desktop, however when i rebooted, nothing was saved (including users I  opened).
At this point better not to elaborate about this but it looks like you rebooted in a live session again, as previously commented. But one step at a time... 

> 3. I'm facing multiple bugs here in Ubuntu, which includes no sound and  having real trouble downloading basic stuff like chrome and flash  because I don't know how to access my root user. Can you please refer me  to any good beginner's manual about managing stuff here?
All in due time. Users inability to do certain things isn't a bug. We'll deal with everything else later, right after we have the full picture from the Boot Repair summary.

---

### Post by tbarhaim on 2020-04-18
here is a link to the report:
[http://paste.ubuntu.com/p/YsR2vfXMhP/](http://paste.ubuntu.com/p/YsR2vfXMhP/)

Btw I used Oracle VirtualBox

---

### Post by CelticWarrior on 2020-04-18
Thank you.

Honestly, it's weird. It seems you still have some DVD or USB with the Ubuntu installer connected. However, this has nothing to do with Virtualbox and again, using Virtualbox wouldn't have changed anything in the boot order.

---

### Post by ajgreeny on 2020-04-18
When the splash screen for VBox appears  quickly hit F12 to choose your boot device from the list.  Somewhere in the list, assuming you have actually installed to the virtual hard disk and not just run a live system in VBox, you should see the virtual hard disk and be able to choose it.

On my VBox the .iso image I use to run the live system, if not removed automatically when rebooting, will need a press of C, though perhaps yours may be different; I can't remember what the virtual hard disk is listed as but I'm sure you'll find it.

PS:
I think your linked report is for your real hardware, not the virtual install, so is no real help.

---

### Post by yancek on 2020-04-18
You have Grub code in the MBR of the first drive (sda, 232GB drive) and it has the core.img file present and is looking for /boot/grub on the first partition which does not exist.  Therefore, it won't boot.  You haven't indicated how you did what you did but it is very unusual that you have a menu.lst file for Grub on sdb1 since Ubuntu hasn't used it for almost ten years.  Note that the second, larger drive (1.8TB) has one partition formatted ntfs which is a windows filesystem and obviously, a Linux system will not run on an ntfs partition. 

Without more explicit and detailed information on what you did in specific steps, it is going to be very difficult to repair the system, if possible at all.  It looks to me like you wrote the iso to your 1.8TB drive which would explain why you can't save any changes as that is an iso9660 read-only filesystem.     Line 220 of boot repair shows that to be the case.  What is/was on the smaller drive?

It looks like you have complete overwritten the windows install.   I don't know what you have available now, but if you have another Linux "live" system on a usb/dvd, I would use that to attempt to rescue data though there isn't much hope of that. Good software to use for this purpose is testdisk which you can get from the link below.  If you use it, make sure you read the Step By Step Instructions before beginning.

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

What appears to have happened is pretty unusual although I have seen it before.  It's a lack of understanding of the basic concepts and user error, not doing enough research on a subject you are unfamiliar with.  Ubuntu has a web site available which explains in detail how to do what you planned/wanted to do and it has been available for years.  See the link below.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajgreeny on 2020-04-18
I think we are all still completely baffled and uncertain what you have actually done to get into this situation.

Virtualbox is an application which will run on just about all platforms, Linux, Windows, Mac (I think, but not sure about that) and possibly others.

Once it is installed you can create a virtual machine of another operating system, or guest OS in virtual hardware, and then run that guest OS without stopping the first or host OS.

So please tell us exactly what you did because when you say you ***"used Virtualbox to switch from Windows."*** it makes no sense at all, as that is not what Virtualbox does; it does not install an operating system to real hardware so as to take the place of another OS.

---

### Post by yancek on 2020-04-18
> I think we are all still completely baffled and uncertain what you have actually done to get into this situation. 

How is a bit baffling to me but what was actually done seems fairly obvious.  The OP download and tried to write an Ubuntu iso to a USB and mistakenly overwrote everything on the 1.8TB drive instead thereby destroying the windows install. This conclusion is based on Information in the boot repair output.


line 25 Boot files: /boot/grub/menu.lst (on sdb1 ntfs fs)  ((Problem here is that Ubuntu has not used Grub Legacy w/menu.lst file since release 9.04-10 years ago))
sda shows no info/partitions  ((No idea what was here)
line 49 shows ntfs on sdb1  ((this is the partition where the Grub boot files are))
lines 34 and 45 show both disks are dos ((Meaninga legacy install of windows))
line 67 /dev/sdb1 ntfs fs LABEL UUI  ((Universal USB Installer))
beginning on line 88-118 show contents of menu.lst for a live system ((Looks like a grub4dos menu entry rather than the original Grub?))
line 205 sdb1 part ntfs 1.8TB UUI (universal usb installer) also referenced on line 21
Line 220 shows sdb1 as ./isodevice which indicates a live system

If you can't recover data w/testdisk I expect the only way to get windows back is to re-install from a DVD/USB.  If you decide to try Ubuntu again, make certain you read the 2nd link in my earlier post before beginning.

---

### Post by ajgreeny on 2020-04-19
You may be right but I think perhaps I have been trying to figure out how Virtualbox comes into this sorry saga; I don't  use a USB install disk to create a VM and never have done it that way, I use the .iso file direct and imagined everybody did the same.

I find the boot repair output rather difficult to decipher always so my comments were related to what was being reported by the OP, rather than the boot repair info.

We will just have to do our best in what are very unfortunate circumstances.

---

