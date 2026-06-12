---
title: "Difficulty moving swap/adding partition"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-10-22
I had a bunch of unused space at the end of my drive so using gparted I manipulated things around until I have this -
```
sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10851    87159633+  83  Linux
/dev/sda2           14431       14946     4144770   82  Linux swap / Solaris
/dev/sda3           10852       14430    28748317+  83  Linux

Partition table entries are not in disk order
```

However nothing I've done either using the Storage Device Manager or editing fstab is allowing me to use sda3. Storage Device Manager just keeps adding a new line to fstab but it doesn't effect the use of the partition. I edited all the extra lines out of fstab but I still don't have it right somehow.  I want any user to be able to read and write the files, but no auto mount on startup. Here's what ftab says currently -
```
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                                       proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /                                           ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none                                        swap  sw                        0  0  
/dev/fd0                                   /media/floppy0                              auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3                                 ext4  users,noauto              0  0
/dev/sda2                                  /UUID=201a5f4d-c1e6-4e39-b21c-f0cf460e1e53  swap  sw                        0  0  
 
```

The second part of this - I followed the instructions on the ubuntu site for moving the swap but I may have missed something. Gparted is not showing the extended bit around the swap. See the attachment to see what I mean.

If someone could point out my mistake(s) here, I'd be grateful.

mystmaiden

---

### Post by enkay009 on 2011-10-22
Your fstab line for /dev/sda3 seems fine.

What happens when you type this?

```
mount /dev/sda3
```Do you get an error message?

[COLOR=Sienna]Also, just curious, why don't you want this mounted on startup?[/COLOR]

---

### Post by Miljet on 2011-10-22
Your fstab file is trying to mount two different swap partitions, one of which no longer exists. I would comment out, or remove, the one that refers to sda5.

---

### Post by mystmaiden on 2011-10-22
Thanks Miljet but commenting that out produced an error message on reboot.

I've also discovered the source of my difficulty with sda3 - it is owned by root. Not sure if that's normal but I've never run into it before. I don't know how to change that.

---

### Post by mystmaiden on 2011-10-22
> **enkay009 said:**
> Your fstab line for /dev/sda3 seems fine.

What happens when you type this?

```
mount /dev/sda3
```Do you get an error message?

[COLOR=Sienna]Also, just curious, why don't you want this mounted on startup?[/COLOR]

Thanks for the reply enkay. It mounts just fine, problem is I can't move any files into it without using gksudo nautilus and entering my password. The only reason I usually set up my extra partion so that it doesn't mount on startup is that it seems to slow things down a bit (this isn't the world's fastest drive) and I only use it to stick backups of media or documents in it once in awhile.

---

### Post by enkay009 on 2011-10-22
Sorry about the post earlier...

How about allowing the userland mount (gvfs-mount) to mount it instead?

If you comment out the line with /dev/sda3, you should be able to mount it with gvfs-mount either through nautilus (it'll appear as an icon) or using gvfs-mount from the command line:

```
gvfs-mount /dev/sda3
```

---

### Post by Miljet on 2011-10-22
It is normal for the mount point to be owned by root. I think that you need to include "user" in your mount options in the fstab file. Take a look at "man fstab" to see what options are available and which you need to use.

---

### Post by mystmaiden on 2011-10-22
> **enkay009 said:**
> Sorry about the post earlier...

How about allowing the userland mount (gvfs-mount) to mount it instead?

If you comment out the line with /dev/sda3, you should be able to mount it with gvfs-mount either through nautilus (it'll appear as an icon) or using gvfs-mount from the command line:

```
gvfs-mount /dev/sda3
```

There's already an icon and it is mountable already. Unfortunately it's the permissions that have gone astray somehow. Will the command you mentioned fixed the permissions? (I can not Unmount it now though, it says I must be root) EDIT - I found the answer on another post here on the forum. Using the command below fixed the permissions.
```
sudo chown <username:username> /place/to/mount -R
```

---

### Post by mystmaiden on 2011-10-23
I think I should have made this separate posts. I got the difficulty with the data partition fixed and proceeded on to the swap file.

I deleted it and made a new one this time inside of an extended partition as it should have been, then checked fstab, and made a couple of adjustments. One of which was obviously way wrong because now I can't boot up. First it gives me an error mounting the swap partition, then an error mounting /  - then it just sits there doing nothing. Is there any way to edit fstab via the live cd so that I can fix the mess I've made?
I tried but it gives me 'you do not have permission to save' Here's fstab as it is now. The difficulty ensued, I believe when I added the word 'none' to the sda5 line (I got that from a website but I can't access bookmarks to show where, since then I've found it might have better been 'swap'

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                                       proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=f752e784-ef82-4653-821c-2221bb33361b  /                                           ext4  defaults                  0  1  
#swap was on /dev/sda5 during installation
UUID=9f7fc64f-4c9b-4fc5-9f94-931c1bb1cde0  none                                        swap  sw                        0  0  
/dev/fd0                                   /media/floppy0                              auto  rw,user,noauto,exec,utf8  0  0  

/dev/sda3                                  /media/sda3                                 ext4  users                     0  0  
/dev/sda2                                  
 
 
 
/dev/sda5        UUID=c4f68369-8213-46a6-a6f0-dc62f27ecd0c                              none swap  sw                0  0  
```

Is there any way to fix this or is there a reformat in my very near future :(

---

### Post by enkay009 on 2011-10-23
You'll need to the edit the file as root from the livecd. You can assume root from the livecd by running this in a terminal:

```
sudo -i
```

From this terminal you can invoke a text editor (like gedit, vi, or nano) to modify the file.

A few things look weird about your fstab.
 
 1. I'm guessing the root partition isn't mounting because the UUID for it has changed.
 
The problem I suspect is that UUID for your root partition (/) has changed. You can the UUID by running this in the terminal:

```
ls -l /dev/disk/by-uuid
```

The UUIDs will be symlinked (symbolically linked) to things like /dev/sda1, /dev/sda2...

When you find the UUID for your disk, check if it's changed. If it hasn't, try mounting by device name instead of UUID (/dev/sda1 instead of UUID=blah-blah-blah...).

So in your fstab, this:

```
UUID=f752e784-ef82-4653-821c-2221bb33361b  /                                           ext4  defaults                  0  1
```

Becomes this...

```
/dev/sda1  /                                           ext4  defaults                  0  1
```

2. The last swap line in your fstab is not in the right format.

From this line...

```
/dev/sda5        UUID=c4f68369-8213-46a6-a6f0-dc62f27ecd0c                              none swap  sw                0  0
```

Get rid of either /dev/sda5 or UUID=... You have one to many arguments and they're confusing the mount.

3. You also have maybe one too many swap lines in your fstab. Make sure everything in your fstab points to something that actually exists. Otherwise you'll slow down you mount process on boot.

---

### Post by mystmaiden on 2011-10-23
Thank you very much, enkay, that's got me up and running again. I used  path for fstab and there were no further errors. I'm not sure why sda1 was giving an error on boot but fixing the swap line on fstab fixed it as well.

---

