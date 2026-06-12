---
title: "data drive access"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jagspc0323 on 2008-06-26
good day

anyone could help me with my problem. i just slaved a hard disk with pre installed freeBSD. the one who installed the freeBSD forgot the password of the root account. and it was set to restriction on the access of data drive. even if i slave it, it says that UNABLE TO MOUNT THE VOLUME. help anyone.

---

### Post by gtdaqua on 2008-06-26
if it is a slave-hdd then you should be able to mount it. What distro are you using your main OS to access the slave hdd?

Whats the output of "sudo fdisk -l"?

---

### Post by jagspc0323 on 2008-06-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   a5  FreeBSD

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006eb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3579    28748286   83  Linux
/dev/sdb2            3580        3738     1277167+   5  Extended
/dev/sdb5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/sdc: 1020 MB, 1020788736 bytes
16 heads, 32 sectors/track, 3894 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x73b40885

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3894      996848    e  W95 FAT16 (LBA)


it is the sudo fdisk -l, it can't be access. im using ubuntu 8.04

---

### Post by gtdaqua on 2008-06-26
> 
it is the sudo fdisk -l, it can't be access. im using ubuntu 8.04


what does that mean?

Your /dev/sda1 is FreeBSD. Change to root and try this:

```

su
mkdir /bsd-drive
mount /dev/sda1 /bsd-drive

```

Let me know how it went.

---

### Post by iaculallad on 2008-06-26
Since you're trying to mount a FreeBSD drive, try this instead:


Your mount point as suggested by gtdaqua:

> /bsd-drive

Can be:

```
sudo mkdir /media/bsd-drive
```

So, to mount it:

```
mount -t ufs -o ufstype=5xbsd /dev/sda1 /media/bsd-drive
```

---

### Post by jagspc0323 on 2008-06-26
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 it is what the system says.

---

