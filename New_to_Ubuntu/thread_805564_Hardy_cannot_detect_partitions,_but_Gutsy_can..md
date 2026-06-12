---
title: "Hardy cannot detect partitions, but Gutsy can."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by RadenMu'az on 2008-05-24
I have just installed Xubuntu 8.04 Hardy Heron.
The problem is, unlike Gutsy, Hardy detects my IDE hd as SCSI and now Thunar cannot detect the hd's partitions.
However, mounting USB stick and its partitions is fine whatsoever.

How do I fix this? Is this because the new kernel in Hardy? :(

---

### Post by alienexplorers on 2008-05-24
Are your drives being mounted in fstab.  Try typing in terminal:
> mount
check to see if your drives are listed and also check the mount points.
If they are not mounted or the mount points are wrong then go into fstab and add your drives.

---

### Post by louieb on 2008-05-24
Check the [**Known Hardy bugs and workaround**]("http://ubuntuforums.org/showthread.php?t=773851") sticky thread in the** General section.  **There is one about sata drives not bing detected.

---

### Post by RadenMu'az on 2008-05-24
> **alienexplorers said:**
> Are your drives being mounted in fstab.  Try typing in terminal:

check to see if your drives are listed and also check the mount points.
If they are not mounted or the mount points are wrong then go into fstab and add your drives.

Uh.. mounted with fstab or not Thunar still cannot detect the partitions

---

### Post by RadenMu'az on 2008-05-24
> **louieb said:**
> Check the [**Known Hardy bugs and workaround**]("http://ubuntuforums.org/showthread.php?t=773851") sticky thread in the** General section.  **There is one about sata drives not bing detected.

After reading workaround for "SATA drives not detected in IDE mode",
I tried 'all_generic_ide' cheatcode at GRUB, but still won't work. :(

---

### Post by RadenMu'az on 2008-05-24
Uhh... this is weird, but I can easily detect and mount the partitions with PCManFM (as root).
However I cannot mount it PCManFM without root privilege.
Thunar meanwhile doesn't detect the partitions at all.

---

