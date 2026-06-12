---
title: "Increase space for Ubuntu"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Keshav2050 on 2012-09-13
I generally use ubuntu more than windows, so I thought to increase the disk space for ubuntu and resized the ntfs partitions of windows to create approximately 162 GiB of unallocated space available for ubuntu in the order:

unallocated  unallocated                 161.93MiB
/dev/sda9    ext4         /              46.74GiB
unallocated  unallocated                 2.00MiB
/dev/sda10   linux-swap                  1.96GiB
unallocated  unallocated                 1.02MiB

Initially I just wanted to increase the size of /, but I got a warning message that if we resize/move root folder os may not boot, I installed boot repair in ubuntu but I don't know if it will work or not, I've also read that we can create a seperate partition for home folder, but the procedure seemed complicated. I'm now really confused if I have to create a seperate partition for home folder or resize the root I don't want to just create home partition for saving settings, but I don't want to loose some applications while upgrading or if I come across any problem and I have to reinstall ubuntu (no big deal even if I loose them though).I even have edubuntu, kubuntu, lubuntu and xubuntu installed.

---

### Post by Bashing-om on 2012-09-13
Keshav2050 ; Hi !

  With all those operating systems installed, this is going to be tricky, not difficult, just be particular/sure about what you are doing.

Firstly, windows tools for windows problems, linux tools for ubuntu situations.

1. So, use the windows disk utilities to resize the ntfs partition. keep in mind can only have a max of 4 primary partitions per disk.
2.Then in the linux install use the command:
```
fdisk -l
```to see your disks layout.
3. With the above info I would suggest to use Gparted to set up the partitions for ubuntu: ( a separate home is a good thing) 
     bearing in mind what disk you are going to boot from  and where you want grub
     installed to, such that all os's are detected and grub updates to be able to boot any.
4. In the install process: at the install process screen choose "something else" , verify the installer installs as you wish, insure the boot flag is set on your boot partition. In the final install screen (final advisement on what the installer is going to install) click on the advanced tab and insure grub is going to be installed at the desired location.

This is over simplified, as you need further assist/advise please ask.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by Keshav2050 on 2012-09-14
The information was given from GParted, I've already resized the ntfs partitions of windows using ubuntu CD, I don't know how to create seperate home partition or if I can resize the root folder directly and use boot-repair from ubuntu CD if it doesn't boot after resizing the root folder.

---

### Post by mips on 2012-09-14
Could you post the output of 'sudo fdisk -l' here.

---

### Post by Keshav2050 on 2012-09-15
sure,

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfeabfeab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157549454    78774696    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       157549516   976771071   409610778    f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda5       157549518   262408191    52429337    7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       262410240   367267839    52428800    7  HPFS/NTFS/exFAT
/dev/sda7       367269888   472129535    52429824    7  HPFS/NTFS/exFAT
/dev/sda8       472131584   535046143    31457280    7  HPFS/NTFS/exFAT
/dev/sda9       874637312   972654591    49008640   83  Linux
/dev/sda10      972658688   976771071     2056192   82  Linux swap / Solaris
```

---

### Post by Keshav2050 on 2012-09-16
The above post is the output of  'sudo fdisk -l'

---

### Post by Bashing-om on 2012-09-16
can not fathom why so many partitions devoted to windows. However the concern is sda9 for ubuntu, and getting it enlarged.
as one can only have 4 primary partitions on each hard drive..... What does Gparted (from the live cd) tell about the partitioning ?

 Suggest using windows disk utility to resize/delete ntfs partitions ...and then ubuntu Gparted to enlarge the sda9 partition (if the system still recognizes the partition as sda9 when deleting a ntfs partition).

  I have a personal preference to run ubuntu in it's own primary partition.
[INDENT]hth <==BDQ 
[/INDENT]

---

### Post by Keshav2050 on 2012-09-18
GParted doesn't warn me about the number of partitions, but only about the booting problem after resizing the root folder.

---

### Post by Keshav2050 on 2012-09-18
Picture of GParted.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=224311&stc=1&d=1347973803[/IMG]

---

### Post by Bashing-om on 2012-09-18
Keshav2050;

  If And/As I read you Gparted=> sda1 is windows, sda2 is a extended partition within windows, all other partitions appear to be logical partitions within the sda2 partition.
that being the case....is ubuntu running in windows as "wubi".
If that is so ...use windows disk utility to expand the sda9 (/) partition into the adjacent 161.93 GiB unallocated space.

[INDENT]still learning even after all these years ==>BDQ

[/INDENT]

---

### Post by YannBuntu on 2012-09-18
hello
> **Keshav2050 said:**
> Picture of GParted.

Seems like you used Gparted from installed session.
Please use Gparted from a Ubuntu liveCD ("Try Ubuntu").

---

### Post by Bashing-om on 2012-09-18
Keshav2050;
  Disregard my last, pending on updated information for further advise.

---

### Post by Keshav2050 on 2012-09-19
I don't think so, I never saw anything related to wubi while installing ubuntu, but it only showed a total 100GiB while installing ubuntu, so I've allocated 50GiB for ubuntu(50%), but then I wondered why, it showed only 100GiB, and tried to find anything related in Google and finally installed GParted and tried to resize the partitions to allocate more space for ubuntu, but I got a warning that I can't resize the root folder as system may not boot(may be if I change the location of the files which aid in booting-which are present in the root folder).

---

### Post by Keshav2050 on 2012-09-19
I've used GParted from live CD, I just posted the picture to show the details.

---

### Post by mips on 2012-09-19
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): [COLOR="red"]512 bytes / 4096 bytes[/COLOR]
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfeabfeab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157549454    78774696    7  HPFS/NTFS/exFAT
[COLOR="Red"]Partition 1 does not start on physical sector boundary.[/COLOR]
/dev/sda2       157549516   976771071   409610778    f  W95 Ext'd (LBA)
[COLOR="red"]Partition 2 does not start on physical sector boundary.[/COLOR]
/dev/sda5       157549518   262408191    52429337    7  HPFS/NTFS/exFAT
[COLOR="Red"]Partition 5 does not start on physical sector boundary.[/COLOR]
```

For starters your hard disk has advanced format 4096-byte sectors to which the partitions are not perfectly aligned. This is not really serious but it has a small performance hit.

Why do you have so many NTFS partitions?

---

### Post by rybnik on 2012-09-19
Is it easy to resize a partition without messing up the OS install?

---

### Post by Keshav2050 on 2012-09-22
Is the no. of partitions in windows a problem? If it is, then I'll delete the partitions. Can I please know if I can resize the root partition directly, without any problems in booting the os, neglecting the warning given by the GParted as told in post #1 and #13, can I use boot-repair if any problem occurs or should I create a new home folder in the unallocated partition to cover the space?

---

### Post by Keshav2050 on 2012-09-24
Can anyone please help me?

---

### Post by mansonfan78 on 2012-09-24
The number of ntfs partitions is unimportant, I have several myself.  You can resize the root partition (/) to be bigger without any problems (you just can't make it smaller).  I would recommend a separate home partition as it will make recovery easier if you encounter any problems in the future.  I have made my root partition bigger and have made a separate home myself without any problems.  If you delete or add any partitions before your root it will change the identifying number of root (sda9) and Ubuntu won't be able to boot without first repairing or reinstalling grub.

---

### Post by mansonfan78 on 2012-09-24
After looking at your screenshot I would move both sda9 and sda10 to the left (gparted will let you do that) and make sda9 at least a little bigger to make sure it doesn't lose any space after it's moved (depending on how your hdd reads blocks, simply moving it without resizing it could result in a slightly different size) and then use the remaining unallocated space for your home.

---

### Post by Bashing-om on 2012-09-24
Guys, let's look at this again.. is not windows using dynamic partitioning ? (fdisk -l output).

 Here is my fdisk to compare (msdos -not windows- partitioned)
sysop1@1204-a:~$ sudo fdisk -l
[sudo] password for sysop1: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1429784      714861   83  Linux
/dev/sda2         1429785    34202384    16386300   83  Linux
/dev/sda3        34202446   976771071   471284313    5  Extended
/dev/sda5        34202448   341397314   153597433+  83  Linux
/dev/sda6       341397378   443795624    51199123+  83  Linux
/dev/sda7       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda8       443811753   597409154    76798701   83  Linux
/dev/sda9       597409792   976771071   189680640   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000945e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   968384511   484191232   83  Linux
/dev/sdc2       968386558   976771071     4192257    5  Extended
/dev/sdc5       968386560   976771071     4192256   82  Linux swap / Solaris
sysop1@1204-a:~$ 

See the difference in the sector size and I/O size//

If this indeed means the op's partitioning is "dynamic" in nature, I will have to do some research and thinking before proceeding.
[INDENT]perhaps overly cautious ?? ==> BDQ

[/INDENT]

---

### Post by Keshav2050 on 2012-09-29
Thanks for all of your suggestions, I did the resized and moved the partitions normally, and it worked fine. I've also installed fedora in another partition, can I share applications like flash or other softwares or home folder? Like in between ubuntu and kubuntu, or should I once again install those? And do both linux and fedora share same linux-swap partition?

---

