---
title: "[SOLVED] Used Space on Just Formatted Second Disk"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by cevatceyhun on 2008-11-20
Hello All,

I'm new to Linux and trying to mount my second HDD. I have used partition editor and disk manager to do this. Everything seems to be OK except one thing: used space indicators.

It says me that I have used ~600MB space on this drive. Yet I have just formatted it. How this is possible?

And a second question is: Why there is a lost+found folder in this new HDD?

Thank you.


PS: I have done a lot of searching on this forum and I hope this isn't repeated question

---

### Post by hyper_ch on 2008-11-20
how big is that drive?

post the output of:

```

sudo fdisk -l

```

and also

```

df -l

```

---

### Post by cevatceyhun on 2008-11-20
Thanks! OK here is the output of "fdisk -l" and "fd -l". The HDD I have mentioned is about 10GB. Notice there is another HDD about 120GB. I plan to mount that one too after successfully mounted this one.


fdisk -l
```
Disk /dev/sda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8b1e8b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2392    19213708+  83  Linux
/dev/sda2            2393        2501      875542+   5  Extended
/dev/sda5            2393        2501      875511   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef8eef8e

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073e7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1229     9871911   83  Linux
```

df -l
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18911932  11033316   6917932  62% /
tmpfs                  1036456         0   1036456   0% /lib/init/rw
varrun                 1036456       344   1036112   1% /var/run
varlock                1036456         0   1036456   0% /var/lock
udev                   1036456      2728   1033728   1% /dev
tmpfs                  1036456       580   1035876   1% /dev/shm
lrm                    1036456      2000   1034456   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdc1              9716796    152900   9070304   2% /media/sdc1

```

---

### Post by Dedoimedo on 2008-11-20
> **cevatceyhun said:**
> Hello All,

I'm new to Linux and trying to mount my second HDD. I have used partition editor and disk manager to do this. Everything seems to be OK except one thing: used space indicators.

It says me that I have used ~600MB space on this drive. Yet I have just formatted it. How this is possible?

And a second question is: Why there is a lost+found folder in this new HDD?

Thank you.


PS: I have done a lot of searching on this forum and I hope this isn't repeated question

Hello,

Lost+found is for files that could not be properly recovered, used, allocated etc for whatever reason - power failure, hardware failure etc.

This is used on ext3 (a journaled filesystem) by the filesystem utilities (like fsck) to correct errors and recover lost files.

Dedoimedo

---

### Post by vanadium on 2008-11-20
There is something wrong with a drive /dev/sdb: It does show up in the output of "sudo fdisk -l" but no partitions are recognized. This would indicate that your attempt to partition and format that drive failed. Just try it again using gparted. Be careful to select /dev/sdb as your working drive.

It is safest to just install gparted in your normal system (i.e. not run it from the live disk). You can do this using Synaptic Package Manager (in the System - Administration menu). Then you cannot accidentely reformat your system partitions.

There is also a small, 10 GB disk listed, /dev/sdc, which you have formatted successfully. File systems have "overhead', this is information needed for the "housekeeping". It is normal that after formatting, some of the space is already used by the file system itself.

---

### Post by cevatceyhun on 2008-11-20
> **vanadium said:**
> There is something wrong with a drive /dev/sdb: It does show up in the output of "sudo fdisk -l" but no partitions are recognized. This would indicate that your attempt to partition and format that drive failed. Just try it again using gparted. Be careful to select /dev/sdb as your working drive.

OK. The problem is with the ~10GB drive. I haven't touched the 120GB drive yet. I plane to do that after this ~10GB drive is OK.


> **vanadium said:**
> It is safest to just install gparted in your normal system (i.e. not run it from the live disk). You can do this using Synaptic Package Manager (in the System - Administration menu). Then you cannot accidentely reformat your system partitions.

I've already done that. Thanks.


> **vanadium said:**
> There is also a small, 10 GB disk listed, /dev/sdc, which you have formatted successfully. File systems have "overhead', this is information needed for the "housekeeping". It is normal that after formatting, some of the space is already used by the file system itself.

It takes about ~600MB. Is it normal? I'm not a computer expert but that is too much. In windows there was no noticable difference.

Meanwhile I keep searching and have found some threads about partition tables. Anyone have an idea about that?

---

### Post by cevatceyhun on 2008-11-20
I have found this thread. vanadium is right, apparently everything was OK from the start. Thank you all!


[http://ge.ubuntuforums.com/showthread.php?t=561202]("http://ge.ubuntuforums.com/showthread.php?t=561202")

---

