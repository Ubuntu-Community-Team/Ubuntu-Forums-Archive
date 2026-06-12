---
title: "Thinking about trying Ubuntu"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by tkaed on 2008-09-01
I have a self built machine that I am planning on purchasing another HD for to run Ubuntu on.

Can I keep it so that my windows HD doesn't read my Ubuntu HD, and vice versa? Or will both have access to the other?

What size/brand HD would you guys recommend for somebody new just messing around with Linux and trying to learn.

Thanks for your time.

---

### Post by schauerlich on 2008-09-01
By default, Windows will not be able to read or write to ext3 (the filesystem Ubuntu uses) and Ubuntu will not be able to write to NTFS (the filesystem Windows uses). So you wouldn't have to do anything besides avoid installing the drivers. What are you worried about?

---

### Post by mlentink on 2008-09-01
It isn't very difficult to set up a dual boot system n which each OS lives in its own separate world. But it's not difficult to create one with peaceful coexistence either. If you want you can have either OS read from and write the other's disk, but that's your choice. Look up the dual boot sections in the wiki and you'll be fine.
As to the HD: as long as it's bigger than about 10 Gigs, compatible with your mobo, you're ok.

---

### Post by halitech on 2008-09-01
> **EDavidBurg said:**
> By default, Windows will not be able to read or write to ext3 (the filesystem Ubuntu uses) and Ubuntu will not be able to write to NTFS (the filesystem Windows uses). So you wouldn't have to do anything besides avoid installing the drivers. What are you worried about?

Ubuntu can indeed read and write to NTFS as I do it daily with an external drive 200gig drive and on other systems when I'm playing around trying to get things installed. Windows can also read and write to ubuntu drives if they are shared in samba or they have a program installed to read ext3 drives.

---

### Post by tkaed on 2008-09-01
Are there any advantages to running a dual boot with 2 hd's vs running 2 os' on a partitioned drive?

---

### Post by WastePotato on 2008-09-01
> **EDavidBurg said:**
> By default, Windows will not be able to read or write to ext3 (the filesystem Ubuntu uses) and Ubuntu will not be able to write to NTFS (the filesystem Windows uses). So you wouldn't have to do anything besides avoid installing the drivers. What are you worried about?

What chu talking 'bout, willis?

Ubuntu reads _and_ writes to my Vista Partition (NTFS), without any problems.

:popcorn:

---

### Post by schauerlich on 2008-09-01
> **halitech said:**
> Ubuntu can indeed read and write to NTFS as I do it daily with an external drive 200gig drive and on other systems when I'm playing around trying to get things installed. Windows can also read and write to ubuntu drives if they are shared in samba or they have a program installed to read ext3 drives.

I don't believe ntfs-3g is installed by default, although I could be wrong.

---

### Post by halitech on 2008-09-01
I don't remember installing it and I've only had the external drive about 4 months

---

### Post by gregphil on 2008-09-01
Windows normally can't read or change a native linux partition, however you can install ubuntu onto a FAT32 partition (which windows could change) or you could install a Windows driver to be able to read ext2 or ext3 native linux partions.  Ubuntu can read, and seems to be able to write, a Windows FAT32 or NTFS disk these days.

The thing to think about is the bootloader.  Which ever operating system is loaded last will try to overwrite the master boot record (the mbr) on the active drive (normally the primary disk).  Thus the linux bootloader, GRUB, can trash the Windows bootloader if you are not careful.

One really safe way to do this, if your mother board supports SATA drives as well as IDE, is to add a SATA drive for the new linux install AND set the BIOS boot order to boot from SCSI (which includes SATA) before the IDE.  Then when you boot from CD and install ubuntu it will put GRUB on the MBR of the SATA drive and leave the MBR of the IDE drive intact.  This will include a GRUB bootloader option to "chain load" the existing Windows disk.  The neat thing here is: if you ever 'uninstall ubuntu' the original windows bootloader will still be there and ready to work as soon as you set the BIOS boot order back to IDE first.

Good luck.

P.S.  Changing the BIOS boot order changes the drive asignemnts GRUB uses, so it will "break" GRUB if you change the BIOS boot order after installing Ubuntu.  This can be fixed by editing /boot/grub/menu.lst but it is tricky and very hard to understand.

---

### Post by WastePotato on 2008-09-01
I think it is, as it was when I got my LiveCD from Shipit.

EDavidBurg, you ain't no 1337 haxx0r. :biggrin:

---

### Post by schauerlich on 2008-09-01
> **WastePotato said:**
> I think it is, as it was when I got my LiveCD from Shipit.

EDavidBurg, you ain't no 1337 haxx0r.

Shh, don't let itachi2 know...

Maybe they started shipping it with ntfs-3g after I downloaded my livecd. I got it the weekend 8.04 came out, and I had to install ntfs-3g when I formatted by external HD NTFS.

---

### Post by palomar on 2008-09-01
Maybe something to take into account: when installing ubuntu on the second harddisk, the ubuntu bootloader will be written on the first (vista) harddisk. For most people this is no big deal, but if you definitely don't want Ubuntu to write on your first harddrive you have to temporary disable the first drive before installing ubuntu (just unplug it or disable it on the bios). After installing Ubuntu re-enable your 'vista' harddrive and use the bios to load from disk 1 or disk 2 (mostly press esc or F11 at boot time, or press DEL and change it).

Using the Ubuntu (grub) bootloader is still easier, though...

---

### Post by tkaed on 2008-09-01
> **tkaed said:**
> Are there any advantages to running a dual boot with 2 hd's vs running 2 os' on a partitioned drive?

Anyone? :)

---

### Post by halitech on 2008-09-01
> Maybe they started shipping it with ntfs-3g after I downloaded my livecd. I got it the weekend 8.04 came out, and I had to install ntfs-3g when I formatted by external HD NTFS.

one problem with that theory Dave, I'm still running 7.10 :D

---

### Post by Paqman on 2008-09-01
> **EDavidBurg said:**
> Ubuntu will not be able to write to NTFS (the filesystem Windows uses).

Actually Ubuntu has been able to write to NTFS partitions since Gutsy.

tkaed: You don't actually need to buy a second disk. You can either partition your current disk, or you can actually install Ubuntu onto your existing Windows NTFS partition. Ubuntu only needs about 10GB of space.

What you might want to think about is how to share your data between the two systems. You'll want to have access to all your music/photos/whatever in both, presumably. If you're going to get a second hard drive it might make sense to put both OSes on one drive, and your data on the other.

---

### Post by schauerlich on 2008-09-01
> **halitech said:**
> one problem with that theory Dave, I'm still running 7.10 :D

Conspiracy!

/me will never admit to being wrong. :)

---

### Post by WastePotato on 2008-09-01
Performance, maybe?

---

### Post by WastePotato on 2008-09-01
> **Paqman said:**
> ....Ubuntu only needs about 10GB of space....

Although I'd say you should have at least 15G to allow comfortable room for expansion eg. Adding programs and different desktops.

---

### Post by halitech on 2008-09-01
> **tkaed said:**
> Are there any advantages to running a dual boot with 2 hd's vs running 2 os' on a partitioned drive?

1 advantage I can think of is if you keep all your data in sync on both drives (2 hd) is if 1 drive dies, you still have your data on the other drive with easy access. 

with 2 OS' on a partitioned drive, if you make a mistake in 1 OS, you run the risk of killing your entire drive (depending on what mistake you make)

you can always do like I do (although I just single boot Ubuntu) is to buy an external drive and back up your important data on it. That way, its backed up and if you need to take data to another location, you unmount it, disconnect 2 cables and away you go :D

---

### Post by elmoosecapitan on 2008-09-01
I have a single HD with three partitions: 1. 10~15GB for Vista, 2. <2GB for Lenovo software, and 3. ~230GB for Ubuntu (To say that I dual-boot is a bit of an overstatement). I have accessed vista a few times and personally have never had an issue with Ubuntu nor Vista with respect to being on the same HD. My friend has a similar set up but Vista has a 40GB partition for WoW; likewise, he has yet to run into any dual-booting issues on his HD.

Long story short, dual-booting on a single HD, or two HDs for that matter, is perfectly safe and compatible.

cheers

---

### Post by billgoldberg on 2008-09-01
> **EDavidBurg said:**
> By default, Windows will not be able to read or write to ext3 (the filesystem Ubuntu uses) and Ubuntu will not be able to write to NTFS (the filesystem Windows uses). So you wouldn't have to do anything besides avoid installing the drivers. What are you worried about?

Not true.

I appriciate you trying to help out, but please be sure that what you are telling is correct.

By default Ubuntu can read/write to a ntfs partition (aka a windows machine).

---

### Post by WastePotato on 2008-09-01
> **elmoosecapitan said:**
> I have a single HD with three partitions: 1. 10~15GB for Vista, 2. <2GB for Lenovo software, and 3. ~230GB for Ubuntu (To say that I dual-boot is a bit of an overstatement). I have accessed vista a few times and personally have never had an issue with Ubuntu nor Vista with respect to being on the same HD. My friend has a similar set up but Vista has a 40GB partition for WoW; likewise, he has yet to run into any dual-booting issues on his HD.

Long story short, dual-booting on a single HD, or two HDs for that matter, is perfectly safe and compatible.

cheers

You got Vista running on 15GB? Good lord.

My base installation was 20GB!

---

### Post by barney385 on 2008-09-01
> **billgoldberg said:**
> not true.

I appriciate you trying to help out, but please be sure that what you are telling is correct.

By default ubuntu can read/write to a ntfs partition (aka a windows machine).

+1

---

