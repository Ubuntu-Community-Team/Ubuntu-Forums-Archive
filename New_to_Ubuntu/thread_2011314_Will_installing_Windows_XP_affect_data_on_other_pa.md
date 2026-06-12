---
title: "Will installing Windows XP affect data on other partitions?"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by KIAaze on 2012-06-27
Hi,

After accidentally nuking my Windows installations months ago, I finally want to reinstall it.
The problem is that I have a lot of data on my disk and no place to back it all up.
I already booted with the Windows XP CD and it offers a choice of partitions on which to install, among which the old NTFS partition on which it used to be and on which I plan to reinstall.

Will installing Windows XP affect data on the other non-NTFS (ext4,swap,etc) partitions?

Note:
I already backed up the MBR and partition table using [http://igurublog.wordpress.com/downloads/script-mbrback/]("http://igurublog.wordpress.com/downloads/script-mbrback/"), so restoring GRUB shouldn't be a problem (in fact I plan to install Kubuntu 12.04 directly afterwards, so that should take care of GRUB anyway).

I'm just worried about my /home data. :s

---

### Post by idoitprone on 2012-06-27
> **KIAaze said:**
> Hi,

After accidentally nuking my Windows installations months ago, I finally want to reinstall it.
The problem is that I have a lot of data on my disk and no place to back it all up.
I already booted with the Windows XP CD and it offers a choice of partitions on which to install, among which the old NTFS partition on which it used to be and on which I plan to reinstall.

Will installing Windows XP affect data on the other non-NTFS (ext4,swap,etc) partitions?

Note:
I already backed up the MBR and partition table using [http://igurublog.wordpress.com/downloads/script-mbrback/](http://igurublog.wordpress.com/downloads/script-mbrback/), so restoring GRUB shouldn't be a problem (in fact I plan to install Kubuntu 12.04 directly afterwards, so that should take care of GRUB anyway).

I'm just worried about my /home data. :s

As long as you pre partition the hdd it should be fine, which you already done. Just reuse the old windows partition. Window tools should not understand linux partitions. Since it doesnt it will nuke the partition table to fix it. However, it shouldnt be a problem as long as you give it free space so it can make a ntfs partiton. Just reinstall grub when your done

---

### Post by oldfred on 2012-06-27
If your data has any value at all you should back it up. While any partition changes, installs can accidentally erase something, that is usually user error. I have installed to the wrong partition, but fortunately it was new and I had not copied my data into it.

The install to NTFS should not over write anything in Ubuntu. Windows does not see the Linux partitions. Sometimes some partitioning tool corrupts partition table but that is not normal and often repairable.

Did I mention that backups are important. :)

You can easily restore the MBR with a liveCD or this gui tool, use the same version liveCD as your install:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration. Also good to run Boot info report as it also documents system in case of issues. You then have a starting point for repairs.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by carl4926 on 2012-06-27
I've never had a problem yet. And I do this sort of thing week after  week.  But caution is required. Backup, I always do, just in case.
Ideally, you should have access to other computers that can let you  access the forum here etc.. to seek guidance if everything goes **** up, because the fact that you are even asking this question suggests a limited understanding.

---

### Post by carl4926 on 2012-06-27
Interesting word filter...

So how do I tell people I have Blue T iTs in my Garden

---

### Post by KIAaze on 2012-06-27
Mmh, so it should work without issues, but backup recommended...

I'm reconsidering how necessary my Windows installation actually is. Maybe this will finally force me to get things working in Wine and Virtualbox.
If I still plan to install it, I might buy a new hard disk first to backup up all my data.

Kubunbtu I might still install directly, since I've done similar things quite often. Just need to make sure I choose the right partition, but that's not too hard. It is probably still a good idea to keep my data on a separate, physically removable disk in the future for peace of mind.

---

### Post by carl4926 on 2012-06-27
> Mmh, so it should work without issues

Only thing is you'll need to re-install grub
Typically I use SuperGrubDisk to boot the Ubuntu intall then do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

---

### Post by KIAaze on 2012-06-29
Ok, bought new external HD, rsynced home to it, reinstalled Windows and then Kubuntu. Windows install didn't affect other partitions at all.

Marking thread as solved.

I'm considering doing some of the following now:
-clone the windows partition (clonezilla?)
-create new windows install disk including all updates (nlite?)
-set up regular backup to external HD (rsync? sbackup? crond/atd?)
If any of you have tips for that, let me know. :)

---

### Post by oldfred on 2012-06-29
I like rsync for current backups, but most important data I periodically burn to a DVD or two. Any copy type backup does not preserve old version. Some do add a setting to rsync to include a date in the top level file name so they have multiple copies like the old father, son , grandfather backup routine.

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

Files to include or exclude from full system backup.
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)
Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by KIAaze on 2012-06-29
Thanks for this extensive list of information. I'll have a look at it. :)

---

### Post by youknowme on 2012-06-29
Things seemed to have changed recently. I once had a emachines pc which came with recovery windows xp discs. Anyway, I could shrink the windows partition and then install linux - but couldn't do it the other way around. That is if i installed linux first and then attempted to install windows alongside - windows would wipe the whole disc.

I guess that things have changed so this is no longer the case - but best thing for you is to get a cheap usb drive and back up your important data, just in case.

---

