---
title: "File system"
date: 2011-10-18
forum: Packaging and Compiling Programs
---

### Post by hosseinz80500 on 2011-10-18
Hi.
    I am confusing. there is exist file system structures stored on     Storage media(such as WD external hard) and also file system in the     Linux kernel.
    what is a difference between these two????
[IMG]http://www.4shared.com/photo/P1MZgOd1/Question.html[/IMG]

---

### Post by MadCow108 on 2011-10-18
file systems are just an abstraction layer between applications and the hardware drivers.
They are usually implemented in the kernel, but do not have to be (virtual filesystem, e.g. fuse)

You can have the same filesystem on your external disk and local disk, its just a matter of setting (although changing the setting requires formating the disk/partition).

You often have fat32 or ntfs on removable media to have better compatibility with windows.
Linux distributions usually use some variant of the ext filesystem but there are many more to choose from.
Here is a list:
[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)

---

### Post by varunendra on 2011-10-19
> **hosseinz80500 said:**
> Hi.
    I am confusing. there is exist file system structures stored on     Storage media(such as WD external hard) and also file system in the     Linux kernel.
    what is a difference between these two????
[IMG]http://www.4shared.com/photo/P1MZgOd1/Question.html[/IMG]
Putting simply - If your partitions don't have a 'Label', they'll appear with generic naming system (xx GB drive: yy GB filesystem).

[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Nautilus-DriveDisplay.jpg[/IMG]

To avoid confusion, just give a suitable name to them using Disk Utility tool (like "WINME" in above screenshot) :)

Hope it eliminates your confusion.

---

### Post by haqking on 2011-10-19
> **hosseinz80500 said:**
> Hi.
    I am confusing. there is exist file system structures stored on     Storage media(such as WD external hard) and also file system in the     Linux kernel.
    what is a difference between these two????
[IMG]http://www.4shared.com/photo/P1MZgOd1/Question.html[/IMG]

There is the FS or filesystem which refers to how your disks or partitions are organised in terms of sectors etc and how files are stored, journalling etc etc.

There is also the FHS or filesystem heirarchy which is the layout/tree of how directories and files are stored on that disk or partition.

[Filesystems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

[Filesystem Heirarchy]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

