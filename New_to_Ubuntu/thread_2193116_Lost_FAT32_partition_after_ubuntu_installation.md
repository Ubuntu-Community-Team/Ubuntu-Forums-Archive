---
title: "Lost FAT32 partition after ubuntu installation"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by rami.hasan on 2013-12-11
HI,,

I have installed ubuntu 12.10 desktop edition into my laptop which has Windows 7 installed, I had one partition spanning the whole hard disk, so when I was installing I thought at some point the installer will prompt for a partition resize option, but it did not. After the installation there was only 2 partitions as in the image attached, and I have lost all my original files on the FAT32 partition.

Please help me on how I can recover from this situation!!

Thank you.

---

### Post by Mark Phelps on 2013-12-11
Can't tell what is inside those partitions, so please boot into Ubuntu,  open a terminal, enter "sudo fdisk 'lu" (lowercase L, not a one) -- and post the results back here.

---

### Post by fantab on 2013-12-11
You can try [Testdisk and Photorec]("http://www.cgsecurity.org/") from Ubuntu DVD/USb... stop using your HDD immediately and boot with Ubuntu DVD/USb.
The above tools don't guarantee 100% recovery. Also the part to the HDD to which Ubuntu was written, will lose DATA for good.
There are other Windows specific tools, like [mini tool]("http://www.minitool-partitionrecovery.com/"), with this tool you can only recover data worth 1Gb for free, if its more then you have pay the licence fee.

---

### Post by rami.hasan on 2013-12-11
Mark, Thank you for your help..
here is the result:

[COLOR=#800000]rami@rami-Satellite-L850-B241:~$ sudo fdisk -lu
[sudo] password for rami: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003bd92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 495.5 GB, 495544434688 bytes
255 heads, 63 sectors/track, 60246 cylinders, total 967860224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 4248 MB, 4248829952 bytes
255 heads, 63 sectors/track, 516 cylinders, total 8298496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table
rami@rami-Satellite-L850-B241:~$ [/COLOR]

---

### Post by rami.hasan on 2013-12-11
fantab, thank you for the tip, I will post the development of my story on this thread.

Thank you again!

---

### Post by oldfred on 2013-12-11
I have never used LVM or LVM with full disk encryption, but that looks like the option you chose. They discontinued the alternative installer that was for RAID & LVM type installs and now integrated it into the standard desktop installer. But then it complicates the standard desktop installer for very new users.
With the alternative installer it always said for LVM erase entire drive and install LVM. With desktop installer it does not say that, but I never have seen what happens after the first screen.
If it never told you it was erasing entire drive please file a bug and post what bug that is. 

[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)
 bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

If you installed LVM with encryption, I am not sure you can recover anything. If not encrypted, the testdisk or photorec may still work.

---

