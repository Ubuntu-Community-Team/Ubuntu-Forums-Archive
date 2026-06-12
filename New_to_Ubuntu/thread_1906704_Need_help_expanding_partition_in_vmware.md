---
title: "Need help expanding partition in vmware"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by ras56 on 2012-01-09
Hello all,

I'm pretty new to linux and need to expand a ubuntu vm disk.  Been fighting this all day and finally decided to see if I can get help. 

I have ubuntu (11.04) desktop running under vmware player (4.0.1 build-528992) on a Win7-64 machine.  The vmware disk file is 16gb with 8.6GB of unused space (as reported by System | Administration | Disk Utility.

[IMG]http://s9.postimage.org/s48hek2pr/Capture.jpg[/IMG]

Most of the help I've seen points me toward gparted to actually change the partition sizes but when I run gparted, it sees one allocated volume.

[IMG]http://s9.postimage.org/8awdlupbz/Capture.jpg[/IMG]

Here is the output from sudo fdisk -l:

Ignoring extra extended partition 3

Disk /dev/sda: 16.1 GB, 16106127360 bytes
255 heads, 63 sectors/track, 1958 cylinders, total 31457280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f173

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    12584959     6291456   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        12587006    14678015     1045505    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3        14683410    31455269     8385930   85  Linux extended
/dev/sda5        12587008    14678015     1045504   82  Linux swap / Solaris

Any pointers on where I should go next?  Thanks for any help....

---

### Post by Double.J on 2012-01-09
Hi there and welcome to the forums!

Gotta admit, I use vbox all the time, but I've not tried changing partitions once installed. You can change them during install though so It must be possibe - have you installed vmware tools? can't see how this'd help, but those tools and additions seem to perfomr miracles!

---

### Post by wildmanne39 on 2012-01-09
Hi, I also use virtualbox if you created the disk as dynamic it will automatically grow when you need it too, if you did not you can not change the size as far as I know, you might be able to point it in another location in vmware settings with the virtual machine shut down, you would not use gparted from with in ubuntu.
Thanks

---

### Post by ras56 on 2012-01-10
Thanks for the reply wildmanne39,

> **wildmanne39 said:**
> Hi, I also use virtualbox if you created the disk as dynamic it will automatically grow when you need it too, if you did not you can not change the size as far as I know, you might be able to point it in another location in vmware settings with the virtual machine shut down, you would not use gparted from with in ubuntu.
Thanks

One question in regard to your reply.  I searched, perhaps not as thoroughly as I could have, but I wasn't able to determine how to figure out if a disk is dynamic.  My vm was created by someone else and they don't remember.  Disk Information from vmware settings says "Disk space is not preallocated for this hard disk." and "Hard disk contents are stored in a single file."  The disk file has extension of .vmdk.

Thanks,
ras56

---

### Post by ras56 on 2012-01-10
Hello gnu/mirow,

Thanks for your input.  I'll try installing the tools and see if that will give me any further options.

ras56

> **gnu/mirow said:**
> Hi there and welcome to the forums!

Gotta admit, I use vbox all the time, but I've not tried changing partitions once installed. You can change them during install though so It must be possibe - have you installed vmware tools? can't see how this'd help, but those tools and additions seem to perfomr miracles!

---

### Post by ras56 on 2012-01-10
Tried installing the vmware tools.  No help there.

I think this is a dynamic volume based on what I'm seeing Also tried resizing the VDMK using the VMWare-Player option to expand.  When I expanded, it increased the size of free space on the /dev/sda drive but Disk Utility won't let me modify any of the partitions and gparted still reports the drive as unallocated.

Any help appreciated....

---

### Post by wildmanne39 on 2012-01-10
Hi, in virtualbox you go into settings storage and it shows the kind of disk that was created.
Thanks

---

