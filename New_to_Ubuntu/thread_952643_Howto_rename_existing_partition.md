---
title: "Howto rename existing partition"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-10-19
I have an internal HDD with only one partition. It's from the days when I used windows. It's even a FAT32 partition. I just wondered if it's possible to rename it from within Ubuntu. I can't seem to find out how. Is this possible?

---

### Post by drs305 on 2008-10-19
You can label FAT32 partitions using mtools. It's not as easy as other formats, but it is possible.  Here is a link. Once you open it, do a search to find the section on FAT32 labelling and mtools:
[Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

Comment: I am sure you have your reasons for keeping the FAT32 format, but there are much better alternatives if you in a strictly linux environment.

---

### Post by stephanvaningen on 2008-10-19
Is it renaming the disk, or renaming how it is called in Ubuntu? I think the latter can be done by changing something in fstab

---

### Post by peakshysteria on 2008-10-19
> **stephanvaningen said:**
> Is it renaming the disk, or renaming how it is called in Ubuntu? I think the latter can be done by changing something in fstab

Yes it's the name of the disc/partition shown in Ubuntu. I want to change the name to something else. mtools seems kinda complicated.

Only running FAT because I forgot to reformat it after buying it. And didn't notice it before installing Ubuntu single boot on all my machines, lol. I thought that Ubuntu would reformat all my drives and not only one. So now I got one Ext3, one NTFS internal and one external in addition to the FAT32.

---

### Post by bodhi.zazen on 2008-10-19
See the link drs305 gave you.

Basically you mount a partition at a "mount point"

just unmount the partition, edit /etc/fstab (with say gksu gedit /etc/fstab) and re-mount the partition, viola.

---

### Post by Kellemora on 2008-10-19
Hi Peak

I'm not sure exactly what you want to change here?

If you want to see the word Ubuntu instead of Filesystem under Computer, just right click and hit rename.

If you want the Hard Drive LABEL changed, you can go to gparted and assign a Label to the Ubuntu Partition.....

BUT BE WARNED, you may ALSO have to go to your Bootloader and PROVIDE the name you changed it to also, else Grub might not find your partition.
It depends on whether Root is listed as a UUID number or if it's listed as root=LABEL, if so, then you would need to change it to root=LABEL=Ubuntu.
I think the default for Ubuntu is to use the UUID number.

TTUL
Gary

---

### Post by kaibob on 2008-10-19
> **peakshysteria said:**
> Yes it's the name of the disc/partition shown in Ubuntu. I want to change the name to something else. mtools seems kinda complicated...

Post deleted by Kaibob

---

