---
title: "error &quot;:E:Can't open /dev/block/mmcblk0p12&quot;"
date: 2011-06-27
forum: Programming Talk
---

### Post by difuiv250385 on 2011-06-27
This is related to the kernel boot up from u-boot on an android phone. 
I have an existing kernel 2.6.35 which is working absolutely fine.
 
 I just modified the partition table of the nand flash to accomodate 2 more images (This partition method i followed from an exising 2.6.32 source code where its works fine ).
 
but I am getting an error at the boot time like **":E:Can't open /dev/block/mmcblk0p12**
**E: failed to mount /cache (No such file or directory)". **
 
 
All I changed is just in the partition table file, init.rc files.
My assumption is the initrd root file system is mounted and after that **its not able to mount mmcblk0p12 **(Here the 12th partition corresponds to an image called misc.img)also its not able to mount the /cache because of ext4 file system related issue. 
 
Can somebody help me to resolve this issue.

---

### Post by difuiv250385 on 2011-06-28
Hi can some one please explain me where in kernel I need to change the emmc partition related things. following is the issue (exactly same issue as mentioned in previous post).
 
I am thinking to change the emmc partition by interchanging the "system" and "userdata" partitions. 
 
Please let me know which file in kernel tree should I make changes in.
 
thanks in advance.

---

### Post by difuiv250385 on 2011-07-21
This was purely a filesystem issue and it got solved when I formated the unmounted partitions through adb shell and restarted the phone.:P

---

