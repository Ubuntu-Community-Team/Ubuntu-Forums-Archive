---
title: "[Solved] Drive Device ID changes everytime i reboot my PC"
date: 2009-07-22
forum: Philippine Team
---

### Post by dodimar on 2009-07-22
I am trying to automount my hard drives using fstab, however, everytime I reboot my system, the device ID (sda and sdb) keeps on changing. I have two (2) physical drives,

```
root@xubuntu-obi:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12f612f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    b  W95 FAT32

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc811c811

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825        8923    40957717+   7  HPFS/NTFS
/dev/sdb3            8924       10011     8739360    5  Extended
/dev/sdb5            8924        9045      979933+  82  Linux swap / Solaris
/dev/sdb6            9046       10011     7759363+  83  Linux
root@xubuntu-obi:~# 

```

after reboot, it will change to 

```
root@xubuntu-obi:~# fdisk -l

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12f612f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    b  W95 FAT32

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc811c811

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        8923    40957717+   7  HPFS/NTFS
/dev/sda3            8924       10011     8739360    5  Extended
/dev/sda5            8924        9045      979933+  82  Linux swap / Solaris
/dev/sda6            9046       10011     7759363+  83  Linux
root@xubuntu-obi:~# 

```

any idea how to fix this?
btw, I am using Xubuntu 8.04.
the fat32 drive is PATA
the NTFS/Linux drive is Sata.

thanks..

---

### Post by loell on 2009-07-22
that's just weird but i guess, that really happens,

found something similar

[http://ubuntuforums.org/showthread.php?t=1080011]("http://ubuntuforums.org/showthread.php?t=1080011")

---

### Post by dodimar on 2009-07-22
> **loell said:**
> that's just weird but i guess, that really happens,

found something similar

[http://ubuntuforums.org/showthread.php?t=1080011]("http://ubuntuforums.org/showthread.php?t=1080011")

does that mean I can't use fstab to automount my drives?

---

### Post by loell on 2009-07-22
not sure, but could highlight the changes from both output? ;)

---

### Post by dodimar on 2009-07-22
```
root@xubuntu-obi:~# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12f612f5

   Device Boot      Start         End      Blocks   Id  System
**/dev/sd[SIZE="6"]a[/SIZE]1**   *           1        4865    39078081    b  W95 FAT32

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc811c811

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1**   *           1        3824    30716248+   7  HPFS/NTFS
**/dev/sdb2   **         3825        8923    40957717+   7  HPFS/NTFS
**/dev/sdb3**            8924       10011     8739360    5  Extended
**/dev/sdb5**            8924        9045      979933+  82  Linux swap / Solaris
**/dev/sdb6**            9046       10011     7759363+  83  Linux
root@xubuntu-obi:~#
```

after reboot

```
root@xubuntu-obi:~# fdisk -l

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12f612f5

   Device Boot      Start         End      Blocks   Id  System
**/dev/sd[SIZE="6"]b[/SIZE]1**   *           1        4865    39078081    b  W95 FAT32

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc811c811

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1 **  *           1        3824    30716248+   7  HPFS/NTFS
**/dev/sda2 **           3825        8923    40957717+   7  HPFS/NTFS
**/dev/sda3 **           8924       10011     8739360    5  Extended
**/dev/sda5**            8924        9045      979933+  82  Linux swap / Solaris
**/dev/sda6**            9046       10011     7759363+  83  Linux
root@xubuntu-obi:~#
```

---

### Post by loell on 2009-07-22
ah I see, :)

not the real fix, but you could make two entries in your fstab addressing both identifiers, it's like automounting the "whichever succeeds".

---

### Post by sisco311 on 2009-07-22
You have to mount the partitions by UUID.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

---

### Post by dodimar on 2009-07-22
> **loell said:**
> ah I see, :)

not the real fix, but you could make two entries in your fstab addressing both identifiers, it's like automounting the "whichever succeeds".

yup,,, I was actually thinking about that...

let me also try sisco311 suggestion... 

thanks guys..

```
reboot
```

---

### Post by dodimar on 2009-07-22
> **sisco311 said:**
> You have to mount the partitions by UUID.

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

UUID did the work.. thanks guys... please mark this SOLVED...

Thanks sir loell and sisco311

---

