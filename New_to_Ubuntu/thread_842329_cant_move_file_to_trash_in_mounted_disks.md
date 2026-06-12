---
title: "cant move file to trash in mounted disks"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by cotiK on 2008-06-27
I surpssngly found out that i cant move files to trash (i can only permanently delete them) in my exteranl ntfs usb disk, and 2 partitions of the same sate drive where my filesystem is in. (one fat, one ntfs). 
i cant think of anything i did that explains this. in the past i could move files to trash in these drives

---

### Post by kaibob on 2008-06-27
> **cotiK said:**
> I surpssngly found out that i cant move files to trash (i can only permanently delete them) in my exteranl ntfs usb disk, and 2 partitions of the same sate drive where my filesystem is in. (one fat, one ntfs). 
i cant think of anything i did that explains this. in the past i could move files to trash in these drives

I enabled the trash function for ntfs and vfat partitions that are mounted by fstab as follows:

1) Backup fstab.

2) Add uid=1000,gid=1000 as options to the partition's fstab entry (see example below). 

3) Create a directory named .Trash-1000 in the partition's root.

4) Restart the computer.

Upon completion of the above, deleted files will be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon will show the deleted files. The panel trash icon does not seem to reliably show the deleted files.

~~~

Example fstab entry
UUID=44B5-9621 /media/store vfat defaults,utf8,umask=007,uid=1000,gid=1000 0 1

---

### Post by Bliepo32 on 2008-06-27
It can also be that your disks are mounted as readonly.

---

### Post by cotiK on 2008-06-27
> **kaibob said:**
> 

Upon completion of the above, deleted files will be placed in a directory named files within the .Trash-1000 directory, and your Ubuntu desktop trash icon will show the deleted files. The panel trash icon does not seem to reliably show the deleted files.

in the past when i deleted a file from these drives it went to a ".trash" hidden folder in that disk. I want that enabled.

---

### Post by cotiK on 2008-06-27
> **Bliepo32 said:**
> It can also be that your disks are mounted as readonly.
&#953; can write files to them

---

### Post by kaibob on 2008-06-27
> **cotiK said:**
> in the past when i deleted a file from these drives it went to a ".trash" hidden folder in that disk. I want that enabled.

cotiK,

I researched this issue back when Hardy was still in beta, and the workaround detailed in my above post worked for me. I didn't care if the hidden file was named .Trash or .Trash-1000.

There was a bug report on this issue, and it may now have a fix that will allow you to do what you want. I don't have a link, but a Google search may lead you to it. Or, perhaps someone else has something that will help you.

kaibob

---

### Post by cotiK on 2008-06-27
> **kaibob said:**
> cotiK,

I researched this issue back when Hardy was still in beta, and the workaround detailed in my above post worked for me. I didn't care if the hidden file was named .Trash or .Trash-1000.

There was a bug report on this issue, and it may now have a fix that will allow you to do what you want. I don't have a link, but a Google search may lead you to it. Or, perhaps someone else has something that will help you.

kaibob

ooohh, so you mean this is a "feature", not a bug?
i just thought that i broke sth. Also the trash-1000 folder you suggest i thaught would appear in my filesystem partition and not the other partitions. (like deleting a file from my usb drive and apearing in trash in my filesystem partiion

anyway, thanks alot!

---

### Post by kaibob on 2008-06-27
> **cotiK said:**
> ooohh, so you mean this is a "feature", not a bug?
i just thought that i broke sth. Also the trash-1000 folder you suggest i thaught would appear in my filesystem partition and not the other partitions. (like deleting a file from my usb drive and apearing in trash in my filesystem partiion

anyway, thanks alot!

No, it's a bug (at least as far as I'm concerned). 

The trash-1000 folder is in the NTFS or FAT partition.

---

