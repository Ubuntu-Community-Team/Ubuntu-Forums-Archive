---
title: "external hard drive wont connect"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by bh89 on 2013-11-10
Hi,

I'm running Ubuntu 12.04, and my western digital external hard drive will not connect. It used to connect before i updated to 12.04 but now it shows this error:
> 
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Any help would be really appreciated because im stuck with this. Thanks very much!

---

### Post by Bashing-om on 2013-11-10
bh89; Hi !

Is it true that the hard disk is formatted as NTFS ? .. If so, take the given advise and take the hard disk to a Window's machine and run Windows' check disk on it.

[INDENT][INDENT]the right tool for the right job
[/INDENT][/INDENT]

---

### Post by linuxguru43 on 2013-11-10
Have you tried this yet?  ```
sudo apt-get install ntfs-config  sudo mkdir -p /etc/hal/fdi/policy
```  Now, launch ntfs-config from the Unity Dash Home. Click Advanced Configuration and check the partitions you want to auto-mount at start-up.

---

### Post by Mark Phelps on 2013-11-11
Unfortunately, there is no Linux equivalent of Windows chkdsk -- so you need to do what Bashing-om already suggested.

---

