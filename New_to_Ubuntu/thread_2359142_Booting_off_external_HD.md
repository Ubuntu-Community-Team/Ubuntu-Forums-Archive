---
title: "Booting off external HD?"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by questerlej on 2017-04-21
Hello,

I am a longtime PC user, having used DOS, Windows, and (to a lesser extent) Mac computers all my life. Long story short, I'm interested in possibly migrating to Ubuntu--specifically Ubuntu MATE--as a new daily driver.

I'm running an ASUS desktop with Windows 10, running in UEFI mode. I'd like to dual boot Ubuntu from an external hard drive by installing it on the drive, then selecting the drive in boot options when I want to run Ubuntu. In other words, I don't want to modify anything at all as far as GRUB goes.

About a year ago, I tried to install a Linux disto (don't remember which one) to an external hard drive, but it didn't work out as planned. I selected the external disk as the destination for the bootloader, but when I disconnected the external, the boot menu still appeared If sand I had to follow some convoluted, drawn out process to remove the entry for GRUB from UEFI, an experience I don't want to have to repeat. I don't know what I did to get the bootloader in the wrong place.

If somebody can provide me with more specific instructions or tips on how to install Ubuntu to an external drive without modifying the bootloader on the default boot drive, I'd be very grateful.

Luke

---

### Post by monkeybrain20122 on 2017-04-21
Sounds like you have installed grub in the wrong partition, you should have installed it in the external drive (typically /dev/sdc or something like that /dev/sda would be the internal hard drive. /dev/sdb would be the usb drive for the installer) When you do the installation you are asked to choose where to install the bootloader from a dropdown menu, sounds like you have missed it and kept the default (/dev/sda, the internal drive typically)

I have experience fixing that kind of things only for Linux multiboot and dualbooting with XP years ago. I am afraid I can't help you with win 10, but I remember with XP you have to use the CD.

---

### Post by ajgreeny on 2017-04-21
One difficulty installing an OS to an external drive on a computer that uses UEFI will be that grub is automatically installed to the EFI partition on the first hard disk no matter where you ask the installer to put it.

There may be ways around this, but I have not dual booted since UEFI appeared on the scene so am not easily able to help personally.  However, see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and hopefully someone who understands the report will come along and be able to help you better than I am able to..

---

### Post by oldfred on 2017-04-21
Only suggestion I have seen to avoid the hassle is to disconnect internal drive, if you can use drive as internal drive or seen as sda.
But if then converted back to external drive, then you still need bootx64.efi (see below).


I regularly install to external flash drives with UEFI boot. And it is a hassle.
       Ubuntu Installer uses wrong bootloader location for USB UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

Since I have Ubuntu as main working install on sda, I have to backup my /EFI/ubuntu folder in ESP on sda. New install always overwrites it.
Then I have to copy the /EFI/ubuntu on sda to sdb and copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi.
UEFI only boots from /EFI/Boot/bootx64.efi. And renamed shim expects to find more files in /EFI/ubuntu so both copies required.
Also reset entry in fstab to correct UUID for sdb's ESP, not default sda's ESP.

Be sure to manually partition and include the ESP, FAT32 with boot flag on external drive. If flash drive I use 100MB, but larger drives use 300 top 500MB for ESP.
Create other partitions / (root), swap, data or anything you want. And then use Something Else. You can select sdb for boot loader install, but I have yet to find it fixed.
When done with install, continue using system and do the copies & rename. And edit fstab.


 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad


 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

 [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

    
Then be sure to use Something Else install option.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

