---
title: "Deleted my EFI Partition - can't boot at all"
date: 2015-10-28
forum: New to Ubuntu
---

### Post by tom214 on 2015-10-28
I’m brand new to Linux and I made a mess of my hard drive trying to undo a dual boot.  I believe I deleted my drive's EFI partition while reinstalling Ubuntu with "remove Windows" option. Here are details:  -had dual boot running with Win 8.1 an Ubuntu 14.04 -tried to reinstall Unbutu (I wanted to do full disk encryption at install) -in the process I chose to remove Win 8.1 and overwrite “all empty partitions” or some such. -the new Ubuntu install said “completed”, but the installed Ubuntu won’t boot – I can only use the  “try Ubuntu” option on USB. -here’s the error message trying to boot without the Ubuntu USB:  “Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key” -used Gparted to remove Windows 8.1 partition.  This is what I see now in Gparted: Unallocated	unallocated	513 MiB	         -	 	                -     - /dev/sda2	ext2		244 MiB	64 MiB	179.07 MiB	boot /dev/sda3	crypt-luks	465 MiB	         -		                -     - Unallocated	unallocated	1.02 MiB 	         -	                          -      -  My laptop is a fairly new Toshiba. I’m able to get into the BIOS settings and I see it uses UEFI. The boot order starts with HDD/SSD. Secure boot and fast boot are disabled.  Am I correct I need to create new EFI system partition? I’ve had great difficulty finding step by step instructions on this. I’m not sure if I can resolve this only with Gparted, or if I need other applications. I’ve seen reference to grub, gdisk, fixdata, MBR, bootmgr, mount point (/boot/efi), etc. but not sure how it all fits together.  Any instructions that cover the whole process would be greatly appreciated, as I'm dead in the water at the moment.  I have limited tech knowledge.  Thanks!

---

### Post by yancek on 2015-10-28
If you removed windows and the EFI partition then you need to create an EFI partition for the Ubuntu files.  If all you want is Ubuntu, you should have an option during the install to use UEFI.  I don't use it myself so don't know if it is necessary to create an efi partition first.  I would doubt that but you can continue to search while waiting for an answer from someone with more knowledge.

---

### Post by ajgreeny on 2015-10-29
Sounds like a case for using Boot-Repair in my signature below, unless you can simply reinstall with the default partition layout given if you let ubuntu install automatically from the DVD or USB.

If you need to keep your current installation and get it to boot, use a live ubuntu system, make a 200MB fat32 partition with gparted from that, and label it EFI and give it the "boot" flag.  See
[https://en.wikipedia.org/wiki/EFI_System_partition](https://en.wikipedia.org/wiki/EFI_System_partition)
[https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition](https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition)

Now you can run the default repair from Boor-Repair and as you no longer have a dual-boot system it may solve your problem.  If it does not help run the boot-info script from that and post back here the pastebin link you are given.

---

### Post by tom214 on 2015-10-30
thanks ajgreeny, I will try your instructions, but since my post I found what looks like other good instructions on how to fix my exact problem (i.e. deleted EFI and Windows partitions).

The instructions I found require using ALT Linux Rescue to boot into my installed Ubuntu 14.04 system, then running a few commands. I got ALT Linux Rescue to run off a DVD and it seems to open o.k. and I end up at this prompt: [root@localhost /]#

 However, every command I type returns the error "root is not in the sudoers file". Any ideas?

---

### Post by ajgreeny on 2015-10-30
No ideas, I'm afraid.
I do not know anything about ALT Linux Rescue.

---

