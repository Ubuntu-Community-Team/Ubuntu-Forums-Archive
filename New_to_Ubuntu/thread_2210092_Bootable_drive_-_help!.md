---
title: "Bootable drive - help!"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by savannah2 on 2014-03-08
Let me start by saying my experience with ubuntu is limited to the last 3 hours, but I'm a windows expert and generally very computer/software savvy. Don't ask me what a partition is though, I couldn't tell you.
I'm trying to create a bootable drive with persistence using a 2TB external hard drive and windows 7. I created a perfectly functional bootable drive from it all of 30 minutes ago, but, not knowing what persistence was, didn't set that up. Upon figuring persistance out and knowing I definitely want it, I scrubbed the drive completely, re formatted to FAT32, and tried multiple times in vain to re-do the bootable drive with universal usb installer. And now, every time I try, whether I have persistence checked or not, I get the error "Error while executing syslinux, your drive won't be bootable." I googled and googled and the only solutions (format to FAT32 [no help] , disable antivirus and allow through firewall [no help]) didn't fix it. What am I doing wrong?

---

### Post by savannah2 on 2014-03-09
Update: Even though it claims to not be bootable, if I actually try to boot it, it doesn't work the first time around but then if I turn the computer off and back on it pulls up a command line version of "do you want to try or install" and if I ht try it will still boot from it.* But then* it automatically takes me to the aforementioned command line "do you want to try or install" *every *time I restart the computer, as if it is automatically booting from the external, and it will only boot windows if I unplug the external. Persistence still didn't work, even though I had it turned on.

---

### Post by slooksterpsv on 2014-03-09
Um... a few questions:
1. Why not install Linux to the 2TB drive or partition it down to install Linux on like 200GB or that? Depending on what you want to do you technically only need an 8GB drive.
2. You used UNETBOOTIN to create the drive, you could try Universal USB Installer to see if that would help.
3. Persistence, I believe if I read correctly you figured it out, if not; persistence is a way to keep your settings, files, installed apps, etc. in a Live environment. It is NOT the same as installing Linux to the system itself.

Do you have a 1GB+ thumb drive? It may be better to use that as I'm not sure but I get the feeling the 2TB drive may have some issues, that way you could install it to the 2TB drive. Be careful of the partitioning though and make sure it doesn't install to the internal drive if you do do this. 

Another thing you can try is when you choose to boot from the external and the options come up you should be able to press a key to modify the boot parameters where you can remove the line quiet from the end. This will allow you to see the output upon boot .I think it's F6, a menu will pop-up hit escape to close the menu then move the cursor and delete the word quiet and try booting that way.

---

### Post by savannah2 on 2014-03-09
1. If I knew how to partition it down, or even exactly what that meant, if I thought it would help I would. As explained earlier, no clue on that front. 
2. I DIDN'T use unetbootin, I did use Universal USB Installer, unetbootin didn't even see that 2TB as existing.  
3. I did figure out what persistence is, that's where most of my pain is coming from. I want a system with persistence and am having the hardest time making that work.

I am aware that I only need 8 GB, the reason I'm using the 2 TB is because I want this system to exist on its own, and I want to be able to use it as a portable computer of sorts and save files on it, using all that space. Only using 200 GB of that space would work for that purpose, but I have literally 0% idea how to do that or what partitioning means.

---

### Post by sudodus on 2014-03-09
Welcome to the Ubuntu Forums :-)

I suggest that you learn by trying to do what you want with a (second?) USB pendrive, and when you know how it works, you can start using the 2TB external hard drive.

If I were you, I would not want a persistent live system on a 2 TB drive, but a ***regular installed system*** (like it were installed in an internal drive). Installed systems are more stable and can be updated/upgraded without limits, while persistent live systems cannot upgrade the kernel, and they get slower with more updates due to an overlay file system. If you want a persistent live system anyway, you should not use the standard method with a loop mounted file system inside a casper-rw file, but instead ***create a partition***, format it to an ext4 file system and add the label **casper-rw**. Then, when you add the [boot option]("https://help.ubuntu.com/community/BootOptions") **persistent**, it will recognize the casper-rw partition and use it for persistence.

A partition is a part of a drive (alias mass storage device) that can be used for a file system or swap (virtual memory). C: and D: are partitions in Windows (on hard disk drives, while A: and B: on floppy disks had the file system directly without any partition structure). Partitions are created with ***gparted*** (from another drive, boot from the Ubuntu install drive, where gparted is available).

Drives (mass storage devices) are named **[FONT=courier new]/dev/sda, /dev/sdb[/FONT]** ... (drive letters a, b ...) and partitions are given numbers

Example with old style MSDOS partition table (GPT does not use extended partitions; GPT must be used with UEFI)
```

/dev/sda1  # primary partition
/dev/sda2  # extended partition
/dev/sda5  # logical partition
/dev/sda6  # logical partition
...

/dev/sdb1  # primary partition
/dev/sdb2  # primary partition
...

```
-o-

The good thing with Ubuntu is that ***installed systems are portable*** as long as you use the built in free drivers (avoid proprietary drivers for graphics and wifi). In other words, they are willing to boot different computers almost like an install CD/DVD/USB drive.

Windows is not portable because Microsoft wants you to pay for each installation, and the whole setup is geared to make an installation locked to a particular computer. (I think it is different with a company license).

-o-

I have better experience with ***Unetbootin*** (than with Universal USB Installer). See this general wiki page

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

and the detailed description in this link

[URL="http://zleap.net/unetbootln-usb-how_to/"]Paul Sutton's Unetbootin how to


[/URL]

---

### Post by sudodus on 2014-03-09
> **savannah2 said:**
> 1. If I knew how to partition it down, or even exactly what that meant, if I thought it would help I would. As explained earlier, no clue on that front. 
2. I DIDN'T use unetbootin, I did use Universal USB Installer, unetbootin didn't even see that 2TB as existing.

I think there is a switch in Unetbootin to only see small drives. Try to untick it, and check if the big drive is recognized! But I would encourage you to make a regular installation instead of a persistent live system.

The installer itself can edit partitions, but I think it is easier to use ***gparted*** before the installation, because the graphic representation is better, so you 'see' what you do.

  > 
3. I did figure out what persistence is, that's where most of my pain is coming from. I want a system with persistence and am having the hardest time making that work.

I am aware that I only need 8 GB, the reason I'm using the 2 TB is because I want this system to exist on its own, and I want to be able to use it as a portable computer of sorts and save files on it, using all that space. Only using 200 GB of that space would work for that purpose, but I have literally 0% idea how to do that or what partitioning means.

And an installed system without any proprietary drivers is portable. I make such systems since several years. See also this link

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by sudodus on 2014-03-09
If you want a system that works with most 64-bit PC systems, this might be a solution:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Persistent_USB_drive_that_works_with_BIOS_and_UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#Persistent_USB_drive_that_works_with_BIOS_and_UEFI)

If you want a system that works with most PC computers (also older computers), but not with UEFI, you should use a ***32-bit system***

And for portability, you get a long way with a ***32 GB USB 3 pendrive*** (with either a persistent live system or an installed system). How much data must be ported?

---

### Post by slooksterpsv on 2014-03-09
I am so sorry I swear I read unetbootin not Universal USB Installer. Well to partition the external drive in Windows, do the following (you'll have to redo the live persistence).
Windows 8/8.1 - Right-click on the task bar where the start button should be/is then click on disk management.
Windows 7 - Click on start and search for diskmgmt.msc

After you run that you'll see something like this:[ATTACH=CONFIG]250989[/ATTACH]

WITH THE USB DRIVE ATTACHED you should see it listed as a 2TB drive. BE VERY CAREFUL HERE.
You can right-click on the 2TB partition and delete it and then create a new simple volume with as much or little data as you want to allocate to it, then allocate the rest as it's own as well.

Quick note on partitions, MBR, and GPT:

Partitions are segments. Think about when you cut a pizza - you're partitioning it. You can put pepperoni on one side and pineapple on the other or your can cut it into different sized partitions. You could do (lets say file systems) a pizza pie on the left half of it (FAT32) and maybe a cream pie on the right (NTFS).
MBR - MBR type drive layouts only allow 4 partitions. No more than that. MBR is pretty much obsolete as of Windows 8, but you can still use MBR as it's very widely used.
GPT - GPT type drive layouts can have more than 4 partitions I'm not sure how many, but I've seen systems with as many as 20 partitions using GPT. So you could do:
5GB, 20GB, 200GB, 200GB, 15GB, 3GB, 2GB, 100GB, partitions on a GPT layout.
On an MBR you can only do 4 so 100GB, 500GB, 500GB, 900GB  - no more.

If you need further assistance with how to use disk management, you'll need to google it, it may be a basic tool but you do need to take caution as you could accidentally wipe out the wrong drive.

---

### Post by savannah2 on 2014-03-09
Wow, this is a lot of (very helpful!) info. If I had been aware I could make a regular system install on an external HD, I'd be doing that! I wasn't even aware that was possible. I suppose then that is what I'm actually trying to do.  I'll look into partitioning down the external now that I understand it LOL. I don't have an exact number for how much data must be ported, this isn't a specific purpose drive, just a nerdy passion project :)

---

### Post by sudodus on 2014-03-09
Well, it is much more convenient to carry a pendrive in the pocket than an external HDD or SSD, even if those can be rather small nowadays. I suggest that you get a fast pendrive, for example Sandisk Extreme 32 GB for this purpose.

You can use the 2TB disk for backup or simply storing photos, music and video files. And if you wish, you can make it bootable.

Before making partitions you should consider, that Windows reads only the first partition on a USB device, so if some data should be available from a Windows computer, the first partition should be formatted with FAT32 or NTFS. This holds for USB HDDs SSDs and pendrives, and at least for older versions of Windows. I don't know about Windows 8. On the other hand, some computers cannot boot, if the boot files are more than 137 GB from the head end. This makes it complicated if you want a full installation of linux, and at the same time have most of the drive available from Windows.

---

### Post by savannah2 on 2014-03-09
Ah -  I see exactly what you mean. It sounds like this would actually be better done with a smaller, perhaps 128GB hard drive. I had one but god only knows where it's gone. I've got a handful of pendrives, so I'll work with those some too. I have a 6 hour road trip ahead of me so I'll be working on this on the road (No LOL, I'm not driving).

---

### Post by sudodus on 2014-03-09
No, the autopilots aren't good enough for that yet :-P

---

### Post by oldfred on 2014-03-09
Some links with details on external or second drive installs.

 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Windows has confused the world with its definition of drive which is no definition at all. You can have two partitions on one physical drive as c: & d: which in Linux is sda1 & sda2. Or you can have two physical drives with c: & d: which in Linux is sda1 & sdb1. Drives are sda, sdb, sdc etc. Partitions are the numbers after the drive letter or sda1, sda2 etc.

Typical Windows 7 installs use all 4 primary partitions on a drive. You have a 100MB (hidden) boot partition, main or c: drive, vendor utility or misc just to use a partition and the vendor recovery which is the image of the install. 


 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

New Windows 8 systems are UEFI boot based and require gpt partitions. Above is all for BIOS with MBR(msdos) partitions.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

How Windows works with BIOS/MBR, shows Vista but applies to all Windows with BIOS.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

