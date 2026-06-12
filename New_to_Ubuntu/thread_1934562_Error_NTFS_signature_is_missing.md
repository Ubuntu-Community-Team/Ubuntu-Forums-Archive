---
title: "Error: NTFS signature is missing"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by vikram91 on 2012-03-02
Hi all, I have dual booted ubuntu and windows 7 long back. Now i have installed backtrack 5R1. Now when i start the pc, in the grub, it shows only backtrack 5 and windows 7 loader. When i select windows 7 loader, then i get the windows boot menu in which the two options are windows 7 and ubuntu. I want to know how to correct this and see all the three oses in a grub.

When i type mount -t ntfs-3g /dev/sda2 mnt/apple, i get error:

NTFS signature is missing
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition(e.g. /dev/sda, not /dev/sda1)? Or the other way around?

can any1 help me in solving these problems.
I would be really thankful

---

### Post by oldfred on 2012-03-02
If sda2 is your NTFS partition, then something over wrote the PBR or partition boot sector. NTFS partitions have to have NTFS data including the same start & end as partition table and if flagged as boot which boot loader to use ntldr for XP or bootmgr for Vista/7. Windows shows unformated or empty NTFS PBR's  as RAW partitions or empty space.

Best to post boot info script. So we can make best choices. NTFS partitions keep a backup of the PBR that can be recovered it the PBR was only overwritten once. Testdisk or some Windows format tools can do a recovery if possible.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

