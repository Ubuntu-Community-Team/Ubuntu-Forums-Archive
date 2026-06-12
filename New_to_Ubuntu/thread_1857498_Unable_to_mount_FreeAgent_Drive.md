---
title: "Unable to mount FreeAgent Drive"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by DayLite on 2011-10-10
This problem is on Ubuntu 10.04

[QUOTEError mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
 SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
 /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.][/QUOTE]

Any suggestions?

---

### Post by Mark Phelps on 2011-10-10
This is nearly always the result of simply disconnecting an External drive, one formatted as NTFS, without Safely Removing it first.  

It is then marked as "dirty" and won't mount again in Linux until AFTER you hook this drive up to a Windows PC and run CHKDSK on it.

---

### Post by DayLite on 2011-10-10
> **Mark Phelps said:**
> This is nearly always the result of simply disconnecting an External drive, one formatted as NTFS, without Safely Removing it first.  

It is then marked as "dirty" and won't mount again in Linux until AFTER you hook this drive up to a Windows PC and run CHKDSK on it.

I forgot to add that it works fine in Windows. Do I still run a CHKDSK ?

---

