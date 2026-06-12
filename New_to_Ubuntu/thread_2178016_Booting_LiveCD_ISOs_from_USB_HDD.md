---
title: "Booting LiveCD ISOs from USB HDD"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by rubbiks on 2013-10-01
Hi

I'm new to Linux and have a possible stupid question regarding booting multiple liveCD ISOs from external HDD. I found this link in the forum ([http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)) and have a few questions.

My first question is, can this be applied to my USB External HDD? and can i use a more up to date Ubuntu live CD? Will i need to format my HDD to EXT4 before hand?

Thanks for any help.
Rubbiks

---

### Post by VMC on 2013-10-01
That's an old topic with some great tips. I'd forgotten about the "[COLOR=#000000]Lua scripting language"[/COLOR] that the op referenced.

To answer your first question, yes it can be applied. Yes, you can use almost any ISO, as long as you know the boot sequence; Arch for example uses different kernel options. 

Regarding Ext4. No, you can and I have used vfat. 

There's a couple of ways of booting ISO directly. Grub2, gurb4dos us what I use.

edit: It looks like the current grub2 has removed 'lua' support due to legal issues. Apparently you can use [grub-extras]("http://lists.gnu.org/archive/html/grub-devel/2009-09/msg00424.html") to get it back.
edit2: This will take some work.  A blog on compiling grub with lua is found [here]("http://linux.xvx.cz/2010/03/using-grub2-and-lua-installed-on-usb.html"). I personally don't need 'lua' support, as I use the loop-back method.

---

### Post by oldfred on 2013-10-01
It does not matter if hard drive or flash drive. I use both flash drives and internal hard drives. And have used NTFS, FAT32, ext4 and on flash ext4 with journal turned off. But I use grub2 to loopmount ISO. Only applies to BIOS not UEFI. And if Linux formatted you will need to open up permissions to make it easier to use.

The boot drive in BIOS is always hd0. Most flash drives have one partition so it would be (hd0,1) but with hard drives it may be any partition or even on another hard drive, so you may have to adjust if grub is installed and booting from one drive and /boot/iso folder is one another drive.

Different versions do have changes. I have only been able to boot Ubuntu desktop versions, not server nor alternative. And they sometimes change something. Most recent use vmlinuz.efi even for BIOS. Examples boot stanza link below also shows that difference.     

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

