---
title: "Cannot get Ubuntu Installation on USB to boot."
date: 2018-06-10
forum: New to Ubuntu
---

### Post by weiluntong on 2018-06-10
Hi,

When I try to boot an installation from USB, my computer says "Boot Failure."

I am trying to install Ubuntu onto a USB stick so that I have Linux on the go. I bought two USB sticks, one for the LiveCD and the other for the actual installation. The steps I took to create the LiveCD were:
[LIST]
[*]Download Ubuntu 18.04 ISO 
[*]Download Rufus 
[*]Burn Ubuntu to USB with Rufus 
[/LIST]
Booting from this runs flawlessly, and I can try Ubuntu, and install from there, which is what I do, after booting into the LiveCD desktop, I inserted my second USB stick and followed these steps:
[LIST]
[*]Double click Install icon on the desktop 
[*]Clicked next until the step where I can choose how to install, which I chose "Something else" 
[*]Chose /dev/sdc (That's what Linux says my second USB stick is) 
[*]Clicked "New Partition Table..." 
[*]Clicked "OK" to the warning 
[*]Added a new partition to /dev/sdc 
[*]Changed mount point to "/" 
[*]Rehighlighted /dev/sdc 
[*]Clicked the dropdown menu for "Device for boot loader installation:" 
[*]Chose /dev/sdc from the dropdown menu 
[*]Finished off installation. 
[/LIST]
After this I shutdown and remove the LiveCD in preparation to boot from the Installation (my second USB stick).

I expected that I would be able to select the Installation from my boot menu and Ubuntu would start up.

What is actually happening is the error I mentioned before: on the computer (a Fujitsu Lifebook T726) that I used to create the Installation, it says "Boot Failure" when I try.

I have two other laptops, a personal laptop (CyberPowerPC Tracer II) and my girlfriend's computer (Lenovo IdeaPad 300) and I've tried both and they both do not even show an error when I try to boot the Installation, I have to reorder the boot menu to boot from USB but after that, they just boot to Windows without displaying anything (despite being able to boot to the LiveCD after rearranging the boot menu). There is an odd behaviour I've seen though. On my Fujitsu Lifebook T726, there is a new boot option called "ubuntu" and when I have the Installation plugged in, using that boot option successfully boots to ubuntu. However, if the Installation is not plugged in, it boots into what I think is grub, it looks like a shell terminal with "GNU GRUB version 2.02" at the top centered and "grub>" to the left of my cursor.

Does anyone know what the issue might be?

---

### Post by yancek on 2018-06-10
Do you have windows installed on the computer?  If so, which version?  If you have windows, is it an EFI or Legacy system?
Did you install Ubuntu as an EFI system or a Legacy system?  If EFI, did you create a separate EFI partition on the USB you installed to?
What boot options do you see in the BIOS?  

Take a look at the Ubuntu documentaion on UEFI at the link below.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sudodus on 2018-06-11
I think you have installed the bootloader 'grub' into the internal drive. If you can disconnect or unplug the internal drive, and then install Ubuntu from the live USB drive (made by Rufus) to the second USB pendrive, 'everything' will be installed into the (second) USB pendrive, and you will get a complete system, that is portable between computers.

There is a detailed description at the following link,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by gordintoronto on 2018-06-11
When you remove the Live USB and reboot, the USB with the installed Ubuntu is no longer SDC.

I have found that life is easier if I use a Live DVD, then the installed USB doesn't jump around.

---

### Post by weiluntong on 2018-06-11
> **yancek said:**
> Do you have windows installed on the computer?  If so, which version?  If you have windows, is it an EFI or Legacy system?
Did you install Ubuntu as an EFI system or a Legacy system?  If EFI, did you create a separate EFI partition on the USB you installed to?
What boot options do you see in the BIOS?  

Take a look at the Ubuntu documentaion on UEFI at the link below.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Hi yancek,
Thanks for the quick reply. I do have Windows and it's Windows 10. It is a UEFI system, and it looks like Ubuntu is installed in UEFI mode. However, I did not create a separate EFI partition on the USB, and the boot options are in this order:
[LIST]
[*]UEFI USB Key
[*]UEFI USB Hard Disk
[*]UEFI USB CD/DVD
[*]UEFI USB Floppy
[*]UEFI Hard Disk: Windows Boot Manager
[*]UEFI Network: IP4 Realtek PCIe GBE Family Controller
[*]UEFI CD/DVD
[/LIST]
Is it just the EFI partition I need to make this work? Is there a way to "fix" this or do I need to scrap it all and do it again with an actual EFI partition to start with? If I do need to start from scratch. Could you help me out? The documentation you sent is a little confusing for me...

---

### Post by weiluntong on 2018-06-11
> **sudodus said:**
> I think you have installed the bootloader 'grub' into the internal drive. If you can disconnect or unplug the internal drive, and then install Ubuntu from the live USB drive (made by Rufus) to the second USB pendrive, 'everything' will be installed into the (second) USB pendrive, and you will get a complete system, that is portable between computers.

There is a detailed description at the following link,

[Boot Ubuntu from external drive]("https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312")

Hi sududos,

Thanks for trying to help. I see that grub exists on the USB drive though, and I'm a little frightened to be pulling out hardware from any of my laptops...

> **gordintoronto said:**
> When you remove the Live USB and reboot, the USB with the installed Ubuntu is no longer SDC.

I have found that life is easier if I use a Live DVD, then the installed USB doesn't jump around.

Hi gordintoronto,

You know, we ran into a problem with installing with a LiveUSB when trying to create a linux server about a week ago that was also solved just by using a Live DVD. However, none of the computers I have access to can read DVDs as they don't have the reader...

---

### Post by yancek on 2018-06-11
It might be better to get boot repair from the link below.  Use the 2nd option to download and run it from the Ubuntu install media.  Make sure you select the option to Create BootInfo Summary and do NOT try to make any repairs.  You should get a link after running boot repair and you can post that here and someone should be able to help.  If you want an EFI boot, you need an EFI partition on the USB and you need the BIOS set to boot EFI.

If you did not create a separate EFI partition on the USB and Ubuntu installed EFI, it probably put its files on the EFI partition already existing.  THis and other info will show with the output of boot repair.  Also, reading through the link below would explain a lot to you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by weiluntong on 2018-06-11
> **yancek said:**
> It might be better to get boot repair from the link below.  Use the 2nd option to download and run it from the Ubuntu install media.  Make sure you select the option to Create BootInfo Summary and do NOT try to make any repairs.  You should get a link after running boot repair and you can post that here and someone should be able to help.  If you want an EFI boot, you need an EFI partition on the USB and you need the BIOS set to boot EFI.

If you did not create a separate EFI partition on the USB and Ubuntu installed EFI, it probably put its files on the EFI partition already existing.  THis and other info will show with the output of boot repair.  Also, reading through the link below would explain a lot to you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

By the install media do you mean the LiveUSB or the Installation? I have a pastebin for the LiveUSB:
[http://paste.ubuntu.com/p/rN6qCtj3MK/](http://paste.ubuntu.com/p/rN6qCtj3MK/)

And another for the install:
[http://paste.ubuntu.com/p/ShwNCwXw8Z/](http://paste.ubuntu.com/p/ShwNCwXw8Z/)

My BIOS for the Fujitsu and CyberPowerPC are both already set to UEFI boot mode. I was looking at the install pastebin, and got curious about my last judgement. Last time I said that the installation was indeed UEFI. This is because the command I typed in, ```
[ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
``` returned "Installed in UEFI mode." However, I also believed that the first verification, "its /etc/fstab file contains an UEFI partition (mount point: /boot/efi)" was true as well. When I looked at the fstab again, that turns out not to be the case. I saw "# /boot/efi was on /dev/sda2 during installation" and assumed that was for my drive, but I'm now pretty sure that is my Windows partition, and I'm pretty sure /dev/sdd1 is my ubuntu drive, which says this: "# / was on /dev/sdd1 during installation" I decided to make a pastebin for my fstab as well. Thank you for all your help so far.

fstab:
[https://paste.ubuntu.com/p/rDNbvFkqKk/](https://paste.ubuntu.com/p/rDNbvFkqKk/)

---

### Post by weiluntong on 2018-06-12
Hi,

I'm just checking in. I actually realized I have one more computer (It's an old desktop that's been collecting dust for so long that I forgot about it and mistook it for a center piece decoration. With it, I was able to try Sudodus's suggestion. This actually did solve my issue, thank you Sudodus. However, Ubuntu is now installed in legacy mode. Tomorrow, I am going to try to convert it from Legacy to EFI using step 2-6 and then step 5-1 from the guide provided by Yancek. I'll reply with results after. Again, thanks to everyone for their help so far.

EDIT: I need to boot into the LiveUSB again to modify the Installation with GParted, but I have a couple questions. If I need to convert my system to EFI, does the LiveUSB have to  be booted in EFI mode as well? Also, there is already a partition on my USB with a mount point at /boot and a boot flag set. I wasn't sure if I could just either erase this partition and replace it with an EFI partition, if I can change it *into* an EFI partition, or if I should create a new partition and leave it alone.

---

### Post by teamvietdev on 2018-06-13
I install from USB

---

### Post by weiluntong on 2018-06-13
> **teamvietdev said:**
> I install from USB

I'm not sure the connection between this reply and helping me. Or maybe you have the same problem? I made an edit in my last post, though hindsight I should have just put my questions here on this new reply...

---

### Post by sudodus on 2018-06-13
> **weiluntong said:**
> ...

EDIT: I need to boot into the LiveUSB again to modify the Installation with GParted, but I have a couple questions. If I need to convert my system to EFI, **does the LiveUSB have to  be booted in EFI mode as well**? Also, there is already a partition on my USB with a mount point at /boot and a boot flag set. I wasn't sure if I could just either erase this partition and replace it with an EFI partition, if I can change it *into* an EFI partition, or if I should create a new partition and leave it alone.

Yes, I think so. At least I think it is easier to install the grub bootloader (including the grub content in the EFI system partition), when you have booted in UEFI mode.

Depending on the system you boot, you might also install the package grub-efi. I think you have to remove the package grub-pc (for BIOS mode) in order to get grub-efi installed in an installed system, but they are allowed to co-exist alongside each other in a live (or persistent live) system.

Maybe the following link can help you,

[Create boot-loading systems for external drives](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Create_boot-loading_systems_for_external_drives)

It is not quite matching what you need, but may help anyway.

An automatic alternative is [Boot Repair](https://help.ubuntu.com/community/Boot-Repair), which might do it, when booted in UEFI mode.

---

