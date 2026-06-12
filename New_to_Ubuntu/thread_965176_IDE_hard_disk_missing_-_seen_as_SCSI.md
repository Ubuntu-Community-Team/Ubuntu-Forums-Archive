---
title: "IDE hard disk missing - seen as SCSI?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by leftfootleashed on 2008-10-31
Hi,

I've just moved to Intrepid, which is installed on my main 250gb SATA drive. Now I need to get at my other 80gb PATA drive to get my data off it, but I can't see it. There is, however, in 'Computer' a SCSI drive that I don't, and never have, owned.

I suspect a problem I had when upgrading is relevant: When I first installed Intrepid, I got an Error 2 from GRUB (disk not found). No amount of tinkering with drive settings in the BIOS got around this, so I disconnected the PATA drive and reinstalled. Now GRUB loads fine, but despite reconnecting my PATA drive and setting it up in the BIOS, I can't see it.

Any suggestions would be great - I'd really appreciate all my data back.

Cheers,
Dave

---

### Post by cariboo on 2008-10-31
Could you paste the output of:

```
sudo fdisk -l
```

In your next post. I think the SCSI disk you mention is probably yout ide hard drive you are missing.

Jim

---

### Post by leftfootleashed on 2008-10-31
Here's the output you requested Jim:

```
Disk /dev/sda: 81.9 GB, 81947525120 bytes
255 heads, 63 sectors/track, 9962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x144f144e

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30028   241199878+  83  Linux
/dev/sdb2           30029       30401     2996122+   5  Extended
/dev/sdb5           30029       30401     2996091   82  Linux swap / Solaris

```

---

