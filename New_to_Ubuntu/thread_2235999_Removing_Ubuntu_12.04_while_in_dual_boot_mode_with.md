---
title: "Removing Ubuntu 12.04 while in dual boot mode with Ubuntu 14.04"
date: 2014-07-24
forum: New to Ubuntu
---

### Post by ganesh-udhayasankar-4 on 2014-07-24
I have installed Ubuntu 12.04 and 14.04 in dual boot mode, where the bootloader shows both the versions of Ubuntu for me to choose manually on the version to load. I did this to test the differences between the two versions and to make a choice among the two as to my preferred version. Well, my personal preference is Ubuntu 14.04 LTS.

Both are running on the same hard disk partitioned into two equal halves. _**I do not want to use GParted**_ to remove Ubuntu 12.04 as it is a very cumbersome process. So any other way of removing Ubuntu 12.04 is deeply appreciated.

I definitely am a novice to Ubuntu. So a detailed step by step guide would help a lot.

---

### Post by plucky on 2014-07-24
> **ganesh-udhayasankar-4 said:**
> I have installed Ubuntu 12.04 and 14.04 in dual boot mode, where the bootloader shows both the versions of Ubuntu for me to choose manually on the version to load. I did this to test the differences between the two versions and to make a choice among the two as to my preferred version. Well, my personal preference is Ubuntu 14.04 LTS.

Both are running on the same hard disk partitioned into two equal halves. _**I do not want to use GParted**_ to remove Ubuntu 12.04 as it is a very cumbersome process. So any other way of removing Ubuntu 12.04 is deeply appreciated.

I definitely am a novice to Ubuntu. So a detThat is the best way of reclaiming the space after you have deleted 12.04 partition.
ailed step by step guide would help a lot.

Re-install 14.04 using the complete hard drive.

That is the best way of reclaiming the space after you have deleted 12.04 partition.

**Why the objection to using Gparted?**

Did you install 12.04 first or 14.04 first?

whichever system you installed last should be the one that owns the MBR and that is the system you do not want to delete.

Good Luck

---

### Post by Bucky Ball on 2014-07-24
Welcome. _Don't _reinstall. Waste of time and effort and totally unnecessary. ;)

Boot to 14.04 and:

```

sudo grub-install /dev/sda
sudo update-grub
```

It may update grub as part of the first command anyway. Can't remember so run that second command in case.

Open Gparted, right click and unmount the 12.04 partition, right click and delete the 12.04 partition.

Open a terminal and:

```
sudo update-grub
```

Reboot. All should be well.

There is absolutely nothing cumbersome about using Gparted to remove the partition and in fact it is probably the easiest and *least* cumbersome way (and a normal way of doing things). Unsure what brought you to the conclusion it was cumbersome. Would you rather use a terminal??? Or boot from a LiveDVD/USB and launch Gparted anyway or use a terminal there (even trickier)?

---

### Post by Impavidus on 2014-07-24
One alternative: Boot 14.04. Make sure 14.04 is in control of grub:```
sudo grub-install /dev/sda
sudo update-grub
```Then mount the 12.04 partition and delete all files from it. You may use the GUI if you wish. Then update grub:```
sudo update-grub
```Now 12.04 is gone and you can reuse its partition for something else. But having your hard drive split in two equally sized partitions may not be very practical, so I would recommend using gparted to remove the 12.04 partition and do something practical with the hard drive.

---

