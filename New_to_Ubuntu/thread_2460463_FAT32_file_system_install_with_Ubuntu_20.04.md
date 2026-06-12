---
title: "FAT32 file system install with Ubuntu 20.04"
date: 2021-04-10
forum: New to Ubuntu
---

### Post by cougarxr7 on 2021-04-10
If I am not mistaken Linux does not support FAT32 files system.
Then why does the Ubuntu 20.04 ISO install writes a fat32 partition?
Formatting and partitioning does not give the options to change these.
Can't install GRUB.

---

### Post by CatKiller on 2021-04-11
> **cougarxr7 said:**
> If I am not mistaken Linux does not support FAT32 files system. 
You are mistaken. FAT doesn't have the features that are required (notably, permissions) to be used for something functional like / or /home, but it can be read from and written to just fine. 
>  Then why does the Ubuntu 20.04 ISO install writes a fat32 partition?
[https://en.wikipedia.org/wiki/EFI_system_partition](https://en.wikipedia.org/wiki/EFI_system_partition)

---

### Post by DuckHook on 2021-04-11
You may be looking at the EFI partition, which does have to be FAT. However, all other partitions would not be FAT. Depending on how you install, they can be any of EXT4, LVM or ZFS, or a combination of these.

CatKiller is correct in that your main system and data partitions cannot be FAT. FAT does not have the required structure or sophistication to house Linux.

---

### Post by cougarxr7 on 2021-04-11
Thanks for the replies!
Not sure exactly how I did it but I got separate partitions on the drive that are not fat and got Ubuntu 20.04 install and grub is working fine. 
Hey just remember, I'm learning here!! I'm learning here!!!
I install ubuntu18.04 1 1/2 years ago on 2 drives. I kept both drives identical  for back up purposes.
What I do not understand is how I managed to install ubuntu on a drive with no partitions.
The recent one I got working with 5 partitions.
Go figure. 
Thanks!

---

### Post by cougarxr7 on 2021-04-11
Trying to upload pics about this.
File upload manager not being cooperative.
Got 1 pic uploaded but not the other one.

---

### Post by grahammechanical on 2021-04-12
It is my thinking that with an UEFI motherboard we get hard drives that have GUID partition tables and the setting up of the GUID Partition table creates the EFI System partition. 

I have a BIOS motherboard with two hard drives. One drive has a GUID Partition table and an EFI System partition (FAT 32) as well as a BIOS boot partition. The other drive has a Master Boot Record partition table and that only has a BIOS boot partition.

Regards

---

