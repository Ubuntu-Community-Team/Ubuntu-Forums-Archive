---
title: "Internal hard drive won't mount even if forced?"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by BanannaSplitzer on 2013-02-24
A friend of mine's Windows laptop has recently started to get a hard drive disk read error whenever the computer boots up, so I made a Live USB of Ubuntu, and at the moment I'm trying to get their stuff off of the hard drive. The hard drive won't mount at all, though, even if I try doing:
    
sudo mount -t ntfs-3g /dev/ sda2/media/external -o force

The hard drive did mount ***once***, but I closed the lid and it shut itself off or something. Anyways, I'm pretty sure that I'm doing everything right, but the hard drive simply won't mount.
Whenever I try to mount the hard drive, I always get this error:

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=766 count=1 br=-1: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Help?

---

### Post by prodigy_ on 2013-02-24
> **BanannaSplitzer said:**
> started to get a hard drive disk read error whenever the computer boots up
Do you mean Windows doesn't boot anymore? If yes, quite possibly the HDD is dead. You could try checking the partition with **chkdsk** but you'll need Windows for that.

---

### Post by BanannaSplitzer on 2013-02-24
Yeah, the hard disk is probably dead. So is there no hope to save it, then?

---

