---
title: "Moving home/jguy to its own partition"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Jguy on 2011-11-18
First off, I've heard rumours that you cannot have any /home/ partitions on an ntfs file system. Is this true? If it is, then this post is done here.

If not, then read on:

I have /dev/sdb1 formatted as an NTFS file system for use on the windows side of my system. It's got all my music, movies, pictures, etc on it. 

Is it possible to redirect or even move the entire /home/jguy folder over to this drive, or even relocate the directory altogether? My ultimate goal would be to use /dev/sdb1 as my /home/jguy home directory. Is this possible with NTFS file system, and if so, how would you do it? Simply mount the device to /home/jguy and copy over all the configuration and system files? I would imagine I would need to chroot or do all of this from the livecd?

Any help would be awesome.

Thanks.

---

### Post by dFlyer on 2011-11-18
As far as I know it's not possible, unless you create a linux partition on the /dev/sdb1. /home is part of the linux file system.

---

### Post by Gone fishing on 2011-11-18
You can't use ntfs for /home as ntfs doesn't support the Linux / UNIX permissions information. However, there are solutions you could symlink your ntfs music folder, documents folder etc into your /home directory. Your music documents etc would then be on your ntfs partition but appear in your /home directory.

Edit 

It would also be possible to format your /dev/sdb1 as ext3 then use it in Windows for My Documents using Ext2 IFS For Windows, but I think my first suggestion is better.

---

### Post by Jguy on 2011-11-18
> **Gone fishing said:**
> You can't use ntfs for /home as ntfs doesn't support the Linux / UNIX permissions information. However, there are solutions you could symlink your ntfs music folder, documents folder etc into your /home directory. Your music documents etc would then be on your ntfs partition but appear in your /home directory.

That's what I remember hearing.

I've tried the symlinks solution previously and I don't think it worked as intended. Maybe I didn't create the links correctly or something else. I also don't think my media player at the time importaed the music properly, I don't remember, it was long ago.

anyway, thanks for the guidance.

---

### Post by Gone fishing on 2011-11-18
You can do it in the gui in nautilus simply go to you ntfs partition and right click and make link. Then drag to your /home partition and rename music - This does work this is what I do.

You will, however, need to make sure your ntfs partition is mounted on boot - the easy way is to use mount manager (available in software center).

---

### Post by ajgreeny on 2011-11-18
Even easier is to drag files from your ntfs partition to your various folders in home with the mouse middle button.  You will see a question mark as you drag, and when you release the middle button you are asked if you want to "move here, copy here, or link here".

Just choose Link and you are done.

---

