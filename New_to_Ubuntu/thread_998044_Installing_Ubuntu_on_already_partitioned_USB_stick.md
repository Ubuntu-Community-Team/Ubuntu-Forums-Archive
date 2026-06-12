---
title: "Installing Ubuntu on already partitioned USB stick"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by karl-arthur on 2008-11-30
Hi, 

A few months ago I tried to make a bootable USBstick with NimbleX, and therefore partitioned the stick to have a filearchive as well. However, I didn't get the ethernet settings to work, and as I didn't really need a bootable USB, I just put it away and didn't look back. But now that intrepid comes with a built in USB installer, I figured I'd give it another shot. 

As far as I can tell, the Ubunutu installer takes care of the partitioning for you, but as my stick is already partitioned, the installer is only interested it what it can do to one of the partitions at a time. Now, one of the partitions on the stick just contains some docs and pics and such, so I'd be perfectly happy using that for saving stuff and just formating the partion now containing NimbleX. But it seems the installer isn't set up for that situation. Also, the sizes of the partitions (1.9gb for the storage one, 2.2 for the NimbleX one) probably aren't optimal anyway.

Could I just set the installer to act as if its going to discard all changes at exit, and later set it to save changes to the other partition? Or do I have to format the entire stick into a single partition first? And if so, how do I do that?  

Tips are appreciated

---

### Post by C.S.Cameron on 2008-12-01
If you are using usb-creator to install to a flash drive with multiple partitions, you should get the choice to install to any of the partitions that are large enough, as long as they are formatted FAT32.
You should only need to erase enough files to allow 700 MB for the O/S plus what you want for persistence.
Note that Windows will only see the first partition on a flash drive.

---

