---
title: "Help with partitionsI"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by sohail.connected on 2013-11-23
Have about 50 gigs up unallocated before my ext4partition. Is it okay if I merge it with my ext4 partition by using bootable easeus partition tool ?? Will grub be affected?? I have dual boot with windows eight and Ubuntu 13.10 will anything happen to them??

---

### Post by Bashing-om on 2013-11-23
sohail.connected; Hi !

> **sohail.connected said:**
> Have about 50 gigs up unallocated before my ext4partition. Is it okay if I merge it with my ext4 partition by using bootable easeus partition tool ?? Will grub be affected?? I have dual boot with windows eight and Ubuntu 13.10 will anything happen to them??

How many of us have any experience with "bootable easeus partition tool " ? I have never heard of it !

Let's begin to answer that question using tools that we are familiar with.
Provide please the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

As well, a screen shot of what GParted (ubuntu's partition editor) portrays would be nice to see.

Be advised - any time one works with partitions - it is Always advised to back up any important data. Strange things can and do happen that can really mess up your week.

With the above we know where that "unallocated" space is and can advise on how to best incorporate it.

[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-11-24
The EASUS tool is most likely a Windows filesystem partitioning tool -- and while it MIGHT work with Linux filesystems, my own experience has been to use Linux tools on Linux filesystems and Windows tools on Windows filesystems.  Much less chance of filesystems getting corrupted if you use the right tools.

---

