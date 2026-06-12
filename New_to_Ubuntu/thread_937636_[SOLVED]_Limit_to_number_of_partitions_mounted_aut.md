---
title: "[SOLVED] Limit to number of partitions mounted automatically?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by mogsmar5 on 2008-10-04
As I store my documents, music, pictures etc. on an OS neutral NTFS partition I need to have it mounted automatically by Ubuntu at startup, so  I added the partition path (is this the correct terminology) to the /etc/fstab file (/dev/sda6). However, after rebooting neither the datat partition nor my windows partition loaded, which was especialyl a problem as my wallpaper and firefox profile are stored on the data partition. When looking at the partitions in GParted it said that all the ones that were meant to be mounted were, but my windows partition (/dev/sda1) had a warning sign next to it. I could not view the files in it from nautilus, and my data partition did not show up in nautilus at all.

The only way I found to fix this was to comment out the line in my fstab telling Ubuntu to mount my data partition autimatically. Here is the line now: #/dev/sda6 /media/ ntfs defaults,umask=007,gid=46 0 0 

Is the reason for this incorrect syntax in the fstab, or is there some limit on the number of partitions I can mount?

---

### Post by Elfy on 2008-10-04
There isn't a limit to my knowledge on how many can be mounted through fstab, it's more likely to be a syntax problem.

First have you a folder to mount the partition in - it looks like you are trying to mount it in /media - make a folder eg /media/ntfs change line in fstab

```
sudo mkdir /media/ntfs
```

Change line in fstab

/dev/sda6 /media/ntfs ntfs-3g defaults,locale=en_US.utf8 0 0

---

### Post by bumanie on 2008-10-04
Either do as forestpixie suggests (Hi forestpixie ):P ) ie make a directory to mount the partition to or > sudo apt-get install ntfs-configGo to Applications --> System Tools --> Ntfs configuration tool and fill in the form that appears. /etc/fstab will be automatically upgraded to reflect what you have entered into the configuration tool.

---

### Post by Elfy on 2008-10-04
> had a warning sign next to itRe-reading I didn't see this last time, if you run a dual boot I would boot with windows and fix the drive problems. If win is gone then you can install ntfsprogs which can be used to fix some problems.

---

