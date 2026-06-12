---
title: "Help mounting internal drives"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by armyben on 2008-05-20
Hi all, I'm having problems mounting a hard drive internally. It was on my girlfriends computer, which has not been turning on lately. I'm trying to get into it so I can save her photos and music, by plugging it into my computer.  She was running Windows XP, and I'm running Ubuntu (Hardy). When I run fdisk -l  at the terminal, I get this:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e57606

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866    5  Extended
/dev/sda2   *         244        1459     9767520   83  Linux
/dev/sda3            1460       30401   232476615   83  Linux
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ba16ba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30514   245103673+   7  HPFS/NTFS




Then when I try to mount it using "mount -t ntfs-3g /dev/sdb1 /media/internal" I get this error message:


Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


I have only been using Ubunutu for a couple of weeks, and am a little stumped. Could anyone point me in the right direction?

---

### Post by utUtu on 2008-05-20
> **armyben said:**
> Hi all, I'm having problems mounting a hard drive internally. It was on my girlfriends computer, which has not been turning on lately. I'm trying to get into it so I can save her photos and music, by plugging it into my computer.  She was running Windows XP, and I'm running Ubuntu (Hardy). When I run fdisk -l  at the terminal, I get this:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e57606

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866    5  Extended
/dev/sda2   *         244        1459     9767520   83  Linux
/dev/sda3            1460       30401   232476615   83  Linux
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ba16ba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30514   245103673+   7  HPFS/NTFS




Then when I try to mount it using "mount -t ntfs-3g /dev/sdb1 /media/internal" I get this error message:


Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.


I have only been using Ubunutu for a couple of weeks, and am a little stumped. Could anyone point me in the right direction?

The -t  option is ntfs  not ntfs-3g.

---

### Post by superprash2003 on 2008-05-20
this usually happens if the windows pc didnt shut down properly when the drive was inserted then.You could insert the drive on a windows machine and shutdown properly and then try mounting

---

