---
title: "problem with external disk"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by redpower1989 on 2011-12-04
Hellow ! after buck buck up my external disk didn't start and give me this message 
> 
Unable to mount manos (manos= my external disk name)

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details. 


In windows works perfect
How can i solve the problem without delete the data?

---

### Post by diablo75 on 2011-12-05
> **redpower1989 said:**
> 
In windows works perfect
How can i solve the problem without delete the data?

The error message describes an inconsistency on the drive somewhere.  Windows tends to ignore some minor errors and only newer versions of Windows will alert you when they are detected.  The easiest way to fix this is to boot into Windows, right-click on the drive letter, click Properties, select the Tools tab, click Check Now and check the top box off and click OK.  This will check the drive for filesystem errors and repair them if possible.  After it's finished, boot back into Ubuntu and see if the problem occurs again.  If it does, repeat these steps but check both options off instead of the top box.  This will take a very long time but it is a far more thorough check.

---

### Post by redpower1989 on 2011-12-05
thanks


> **diablo75 said:**
> The error message describes an inconsistency on the drive somewhere.  Windows tends to ignore some minor errors and only newer versions of Windows will alert you when they are detected.  The easiest way to fix this is to boot into Windows, right-click on the drive letter, click Properties, select the Tools tab, click Check Now and check the top box off and click OK.  This will check the drive for filesystem errors and repair them if possible.  After it's finished, boot back into Ubuntu and see if the problem occurs again.  If it does, repeat these steps but check both options off instead of the top box.  This will take a very long time but it is a far more thorough check.

---

