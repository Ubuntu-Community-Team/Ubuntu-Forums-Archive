---
title: "Ubuntu thumbdrive, Windows can't see FAT32 partition."
date: 2008-09-07
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-07
I have installed Ubuntu on a 16GB thumbdrive.
I have installed a FAT32 partition so that I can also use the thumbdrive as a thumbdrive.
Windows only seems to see the ext3 partition and wants to format it.
Windows disk management sees the FAT partition but can't do anything with it.
I've tried adding the FAT partition when installing Ubuntu but the installation won't complete, trouble with language pack.

---

### Post by billgoldberg on 2008-09-07
> **C.S.Cameron said:**
> I have installed Ubuntu on a 16GB thumbdrive.
I have installed a FAT32 partition so that I can also use the thumbdrive as a thumbdrive.
Windows only seems to see the ext3 partition and wants to format it.
Windows disk management sees the FAT partition but can't do anything with it.
I've tried adding the FAT partition when installing Ubuntu but the installation won't complete, trouble with language pack.

Delete the fat parition.

In windows, you can create a fat32 partition form the free space. I'm pretty sure windows will be able to read it then.

---

### Post by C.S.Cameron on 2008-09-07
When I delete the partition Windows Disk Management sees it as Unallocated space on Disk 5.
Won't let me do anything with it, only delete (M:) my Ubuntu partition.

---

### Post by bumanie on 2008-09-07
Most thumbdrives are formatted with FAT 16. That may be the problem. Also, you could try gparted to format the drive - from within ubuntu or from the ubuntu live cd > sudo apt-get install gpartedThen look under System --> Administration --> Partition Editor. If from within ubuntu - note the thumbdrive must be unmounted (this will automatically be the case from the ubuntu live cd if the thumbdrive is already in the computer at boot. Gparted live cd loads with all drives unmounted [if my memory serves me correctly]). You can download and burn a stand-alone gparted live cd from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"). A drive cannot be formatted if it is mounted.

---

### Post by mister_pink on 2008-09-07
I don't know if there's any truth to this at all, but I remember being told when I made my live pen drive that windows can't see more than one partition on external disks. Can anyone confirm that? 

If so, the only solution would be to put ubuntu at the end of the disk seeing as it doesnt care. You'll have to change the bootloader on it though.

---

### Post by C.S.Cameron on 2008-09-07
I've tried partitions every which way.
I only seem to finalize Ubuntu installation using guided full disk.
If I install to guided free space I get space errors.
If I use manual to partition the installation runs to ~97% then dies during clean up, something about language pack was the last error message.
At this point windows still sees space on the disk, but Ubuntu won't boot even though a good portion of the files are there.

I'm wondering if anyone else who is booting from thumbdrive has managed to get a partition recognized by windows?

---

