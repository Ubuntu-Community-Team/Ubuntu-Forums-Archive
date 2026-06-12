---
title: "Mounted Disks Disappear in every boot"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gaffurabi on 2008-04-25
i have ntfs windows xp partitions and they are shown in "places" in ubuntu 8.04. i create their shortcuts on desktop but everytime i boot they disappear (on ubuntu 7.10 there was no such problem)
any solution?

---

### Post by kpkeerthi on 2008-04-25
Unless the NTFS partitions are added to /etc/fstab, they will not be mounted at boot time. When you click on the one from "places" it gets mounted on-demand but will not stick across reboots.

Do you want to have it added to /etc/fstab?

---

### Post by gaffurabi on 2008-04-25
yes i would like to have 'em added to etc/fstab..but how? :(

---

### Post by TeoBigusGeekus on 2008-04-25
[http://ubuntuforums.org/showthread.php?t=762027]("http://ubuntuforums.org/showthread.php?t=762027")

---

### Post by kpkeerthi on 2008-04-25
> **gaffurabi said:**
> yes i would like to have 'em added to etc/fstab..but how? :(

Can you post the output of ```
 sudo fdisk -l
``` and let me know the partitions you want automounted.

---

### Post by Jimmy9pints on 2008-04-25
Follow this no-nonesense guide:
[http://ubuntuforums.org/showthread.php?t=761373](http://ubuntuforums.org/showthread.php?t=761373)

Cheers

---

### Post by kpkeerthi on 2008-04-25
> **Jimmy9pints said:**
> Follow this no-nonesense guide:
[http://ubuntuforums.org/showthread.php?t=761373](http://ubuntuforums.org/showthread.php?t=761373)

Cheers

LOL!. I was searching for that. Glad you posted that.

---

### Post by Jimmy9pints on 2008-04-25
Follow this no-nonesense guide:
[http://ubuntuforums.org/showthread.php?t=761373](http://ubuntuforums.org/showthread.php?t=761373)

Cheers

---

### Post by gaffurabi on 2008-04-25
> **kpkeerthi said:**
> Can you post the output of ```
 sudo fdisk -l
``` and let me know the partitions you want automounted.

here is the output:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0de30de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1436    11534638+   7  HPFS/NTFS
/dev/sda2            1437       19457   144753682+   5  Extended
/dev/sda5            1437       17761   131130531    7  HPFS/NTFS
/dev/sda6           17762       18134     2996091   82  Linux swap / Solaris
/dev/sda7           18135       19457    10626966   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6a4f6a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS
/dev/sdb2            9729       19456    78140160    f  W95 Ext'd (LBA)
/dev/sdb5            9729       18935    73955196    7  HPFS/NTFS
/dev/sdb6           18936       19456     4184901    7  HPFS/NTFS

```

---

### Post by kpkeerthi on 2008-04-25
Follow the link posted earlier. 

Here it is again if you need
[http://ubuntuforums.org/showpost.php?p=4757851&postcount=6](http://ubuntuforums.org/showpost.php?p=4757851&postcount=6)

---

