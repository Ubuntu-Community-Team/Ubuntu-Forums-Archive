---
title: "Partition type: Linux, Content: Fat 32 - why?"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by clearski on 2013-04-24
I had a 4GB  stick plugged into my computer.

I typed:

```
sudo fdisk -l #it showed me that the stick was recognized as /dev/sdb 

sudo fdisk /dev/sdb #then typed "n" to create a new primary partition, and "w" to write changes to disk.

sudo mkfs -t msdos /dev/sdb1 #everything went fine

sudo mount /dev/sdb1 /media/stick #/stick was already created
sudo cp ~/Desktop/somefile /media/stick/ #got the file here

sudo fdisk -l
```

And here comes my question, because fdisk shows me that the System is Linux. 

    ```
Device Boot         Start            End         Blocks      Id     System
/dev/sdb1           2048         8027789         4012871     83      Linux
```

I don't have a PC right now to check, however I started *Disks *and it also said "Partition type: Linux", but contents "Fat - 32 bit version".

What exactly is that "Partition type: Linux" and why is it set to Linux when the content is set to FAT? I didn't do any ext* formatting.

Sorry for the dumb question, but I don't get it. Creating a partition from Linux is different from creating a partition from another OS? Is there any fingerprint of the OS?

---

### Post by Mark Phelps on 2013-04-24
FAT 32 is used both by Linux and by Windows; unlike NTFS, it is not a Windows-only filesystem.

---

### Post by clearski on 2013-04-24
> **Mark Phelps said:**
> FAT 32 is used both by Linux and by Windows; unlike NTFS, it is not a Windows-only filesystem.

You mean it's not a sort of proprietary filesystem or it's accesible on both OSes and Linux Fat32 means it is a Linux made FAT32 partition?

---

### Post by grahammechanical on 2013-04-24
I have a USB stick with Ubuntu installed on it. I used Startup Disk Creator in Ubuntu to create the USB bootable Ubuntu stick and that has a FAT32 partition type. Mmany Linux install USB sticks will be created in Windows and so it would be a FAT32 partition or nothing. It could that the Linux developers continued in the same pattern.

I think you will find that the FAT file system is not proprietary. Either that or there was greater competition in those days and having an incompatible file system might limit sales of Microsoft DOS. Certainly it was IBM that set many of the standards with Microsoft playing along with IBM.

---

### Post by clearski on 2013-04-24
> **grahammechanical said:**
> I have a USB stick with Ubuntu installed on it. I used Startup Disk Creator in Ubuntu to create the USB bootable Ubuntu stick and that has a FAT32 partition type. Mmany Linux install USB sticks will be created in Windows and so it would be a FAT32 partition or nothing. It could that the Linux developers continued in the same pattern.

I think you will find that the FAT file system is not proprietary. Either that or there was greater competition in those days and having an incompatible file system might limit sales of Microsoft DOS. Certainly it was IBM that set many of the standards with Microsoft playing along with IBM.

I don't want to get too much into the history of FAT and MS inasmuch as the first gets very technical, and the second is not interesting. :) 

If my FAT / MSDOS formatted usb stick is seen by a computer running Windows, that's just fine. But I'll check it out tomorrow morning on a computer which hasn't got any Linux distro, because I want to see if it says anything about Linux partitioning the stick. That would be nice. :)

Thanks!

---

