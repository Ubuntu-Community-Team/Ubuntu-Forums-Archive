---
title: "Disappearing internal hard drive"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by pat4 on 2013-08-26
Hi,
I am new to Ubuntu - still trying to get my head around the system. I have aproblem that is bugging me and I hope someone can help. I am using v12.04 LTS.

My computer is fitted with two  1 TB hard drives - one is used as the system disc the other is used for storage and backups. When I boot the machine the second hard drive - the backup one - doesn't always appear in the left hand panel of the "home folder" list..

This seems to be intermittent. Occasionally it is there but more often than not I can't see the drive listed. I have checked in BIOS and all SATA channels are enabled. When the drive does appear I can access it OK and have data stored on the disc. Once I have access I have no problems in managing the stored data. 

A little research told me that there may be a problem with "GRUB" (?) and a suggestion to run a command to check that the latest version was installed - I did and it is. 

As the disc is not visible in the panel in home folder, I don't know how to access the disc. 

Any and all help appreciated.

Many thanks.

---

### Post by sandyd on 2013-08-26
> **pat4 said:**
> Hi,
I am new to Ubuntu - still trying to get my head around the system. I have aproblem that is bugging me and I hope someone can help. I am using v12.04 LTS.

My computer is fitted with two  1 TB hard drives - one is used as the system disc the other is used for storage and backups. When I boot the machine the second hard drive - the backup one - doesn't always appear in the left hand panel of the "home folder" list..

This seems to be intermittent. Occasionally it is there but more often than not I can't see the drive listed. I have checked in BIOS and all SATA channels are enabled. When the drive does appear I can access it OK and have data stored on the disc. Once I have access I have no problems in managing the stored data. 

A little research told me that there may be a problem with "GRUB" (?) and a suggestion to run a command to check that the latest version was installed - I did and it is. 

As the disc is not visible in the panel in home folder, I don't know how to access the disc. 

Any and all help appreciated.

Many thanks.

When the disk does not show up, can you post the output of
```

lshw
sudo fdisk -l
```

Thanks.

---

### Post by pat4 on 2013-08-28
Thanks for the response... This problem now seems to be resolved.

Thread cvan be closed.

---

### Post by deadflowr on 2013-08-28
It might help others if you post what the resolution was.

---

