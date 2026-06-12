---
title: "XP can't find HDD"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by AOZ on 2008-07-16
I've been using ubuntu for about a year now and i am very happy with it. however there are some things that i need XP for such as my iPod touch, MS SQL (work), Visual studio TFS (work again) and a few games. So i made a 50GB partition for windows to be on leaving a bit over 60GB for linux. everything went fine but when i try to install XP it says it can't find any HDDs to install on and quits setup imediatly. whats going on? I've been searchign google and they all say to enter the bios and make somehtign compatible but i found no such option. any help would be greatly appreciated

---

### Post by Fire_Chief on 2008-07-16
Is your hard drive SATA? If so, you can either set the BIOS to offer compatibility features on the SATA drive (IDE emulation or something like that) or you add the driver to XP during setup (press F6 at the beginning when prompted to add a driver). The driver will need to be on a floppy disk for XP setup to read it properly. If you can do it, the driver is a better way to go for performance and simplicity.

Cheers!

Edit: Be aware that installing XP *after* you have an existing Ubuntu installation will prevent you from booting into Ubuntu. You will have to re-write the MBR on the disk to point to GRUB again so you can manage dual booting.

---

### Post by alienexplorers on 2008-07-16
I tried one time installing XP and used gparted to create a NTFS file system.  Exited gparted, rebooted, and the XP disk could not find anywhere to put XP.  Next time I tried doing this I formatted the XP partition to FAT32 using gparted.  I rebooted and loaded up the old XP CD and low and behold it found the partition and loaded.  I don't know why it did not work with the NTFS partition, but it liked the FAT32 [artition.  I guess it's one of those windows mysteries.

Note: I was using an IDE ATA drive.

---

### Post by AOZ on 2008-07-16
I know it's SATA but im not sure where to get the drivers. Its on a toshiba tecra A9 laptop btw so im nto sure on the exact HDD. i think its fujitsu? not too sure...

---

### Post by Fire_Chief on 2008-07-16
More specifically, you want the SATA Chipset drivers. 

See here for more info
[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=30136&tstart=75]("http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=30136&tstart=75")

Cheers!

---

### Post by Tomatz on 2008-07-16
The drive/partition needs to be RAW (unformatted), fat or ntfs for the windows installer to see it. Use gparted to format it to fat and it should work ;)

---

### Post by jerome1232 on 2008-07-16
Just to add in I get that problem of windows not having the driver for my sata controller, so using this guide [http://lifehacker.com/386526/slipstream-service-pack-3-into-your-windows-xp-installation-cd](http://lifehacker.com/386526/slipstream-service-pack-3-into-your-windows-xp-installation-cd) I slipstreamed the drivers and created my own xp installation disk (I don't have a floppy drive to add them in during the install) Made it completely automated while I was at it, and I don't have to install a single driver once xp is installed (I integrated them all into the install). It's nice to have.

---

### Post by Fire_Chief on 2008-07-16
> **Tomatz said:**
> The drive/partition needs to be RAW (unformatted), fat or ntfs for the windows installer to see it. Use gparted to format it to fat and it should work ;)

No, it really doesn't. I've installed XP on many systems that had partitions XP did not recognize. They appear as unknown filesystem but do show the correct sizes. They can be deleted and recreated during XP setup.

---

### Post by Tomatz on 2008-07-16
> **Fire_Chief said:**
> No, it really doesn't. I've installed XP on many systems that had partitions XP did not recognize. They appear as unknown filesystem but do show the correct sizes. They can be deleted and recreated during XP setup.

Weird xp doesn't usually pick up non windows filesystems? I'm not saying you are wrong, just that in my experence this isn't the case. 

I wonder if this is different when using versions of xp?

---

### Post by Fire_Chief on 2008-07-16
On second thought, I may be confusing XP with Windows Server 2003. I know Server 2003 does that and I thought I remembered XP operating the same way but perhaps not. Your advice to format the partition certainly doesn't hurt the process at all. :popcorn:

Cheers!

---

### Post by AOZ on 2008-07-16
So i've spent the last few hours tryign everythign but nothign will work. I dont have a Floppy drive on this laptop so i tried with a usb but that didt work. Theres nothign in the BIOS that i can set compatible IDE or whatever. ANythign else i can try?

---

### Post by jerome1232 on 2008-07-16
If you don't have a floppy drive you will have to integrate the drivers into an install disc as xp will only take those drivers via floppy.

---

