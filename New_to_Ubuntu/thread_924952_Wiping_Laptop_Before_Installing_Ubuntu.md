---
title: "Wiping Laptop Before Installing Ubuntu?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ealrgrey on 2008-09-20
Hi guys. I have a good (Vista) laptop which I want to wipe clean and install Ubuntu 8.04.1 on. I have never done this before and am fairly clueless. My question is what is the best way to completely wipe the laptop before I install Ubuntu? I have read about a program called dban which will nuke the drive, but I have also read about reformatting and am unsure if these are different things. If I use dban to nuke the drive does it then need formatting? If so how do I do that? Or will the Ubuntu CD do that?

Or, if I just stick the Ubuntu CD in, boot it up and click Install, will that clean the hard drive for me?

If it makes any difference, I would prefer the hard drive be safely cleaned, such that no data is retrievable.

Obv this is a very dumb question so thanks very much if you take the time to answer it.

---

### Post by hellion0 on 2008-09-20
Installing Ubuntu using the entire disk will wipe out Vista just that easily, should that be your aim.

However, since it seems like you want to totally wipe out the drive first, you may want to look at zeroing it out (overwriting all data with zeros, then repartitioning it as needed).

Once the data's overwritten in such a way, there's no getting it back whatsoever.

---

### Post by lswest on 2008-09-20
The above post is correct, and as an extra bit of info: the more you use the new install, the harder it is to retrieve any data from the Vista install, as you'll be writing over the bytes previously used to hold Vista data.

---

### Post by Elfy on 2008-09-20
If you wanted the drive to be clean before you install you could use dban

[http://www.dban.org/](http://www.dban.org/)

---

### Post by ealrgrey on 2008-09-20
Okay thanks a lot! Just to confirm, installing using the whole drive will delete all of my files as well as the Vista software? I mean, Ubuntu won't try to merge my documents etc into itself for the convenience of switching from windows (which would be useful if I was keeping the laptop for myself)?

---

### Post by MegaJim on 2008-09-20
Ubuntu can repartition your disks and overwrite the MBR with the GRUB bootloader, but that will not destroy any 'hidden' partitions.

If you want to delete some confidential data, consider using the ubuntu live cd and using the shred command, you can find out how to use it by typing this in the terminal

```
man shred
```

If you just want to zero your drive, you can use this command which will overwrite every bit on the disk, including MBR, partition tables and data, but it will not obfuscate in the way that shred does:

```
dd if=/dev/zero of=/dev/hda
```

Where hda is the name of the disk you want to zero.  You can get a list of the disks detected by ubuntu using the command

```
sudo fdisk -l
```

Each of these actions is irreversible, so be sure you want to do so before executing them.

---

### Post by Trebaruna on 2008-09-20
If you really want the data to be irretrievable you will need to invest some time, and you need to consider whether it's worth the time and effort, i.e. who are you trying to protect against? A single format (not quick format, properly write zeroes to the entire drive) will get rid of the data for most purposes. 
If, however, your adversary has expensive tools to analyze harddrives he/she could still piece together what you had on the drive. You can defend against that by formatting several times and using different bit patterns, but this takes much longer. The chances of someone going to such great lengths are very, very slim. You'd have to had something like nuclear secrets on your laptop.
Basically, one format will do the trick. To be honest, I don't know of any software, readily, that can do this, although I do know there are lots of programs that will do the trick. DBAN will probably work, maybe gparted (included in the LiveCD) does it. I know how to do it from the commandline:
```
sudo dd if=/dev/zero of=/dev/sdX
```where X is the letter of the physical drive (if you have just one drive, it will be 'a'). You need sudo because you want to access the harddrive directly.
**Be _extremely_ careful!** This will write your entire drive full of zeroes! **Your data will be gone!** If you have additional drives, triple check to see you've selected the right one.

EDIT: Wow, I need to type faster!

---

### Post by hellion0 on 2008-09-20
To get technical, let's assume you use the whole hard disk Vista's on to install Ubuntu.

Formatting, especially to a new filesystem like you would be doing if you install any variant of Linux, will basically mark all data on that drive for deletion, then overwrite it freely. As you add data to the drive, it will continue to overwrite what was previously there under the old install. Once data's overwritten, it cannot be retrieved in any way.

As opposed to simply "deleting" files, which marks them to be freely overwritten, but doesn't do so on its own, so the data could still be retrieved.

---

### Post by ealrgrey on 2008-09-20
Thanks very much for your help everyone. So if I decide to run DBAN before I install Ubuntu, it would go:

Step 1: Run DBAN from boot disc
Step 2: ?????
Step 3: Run Ubuntu from boot disc

Is there a step 2?

---

### Post by ealrgrey on 2008-09-20
> **ealrgrey said:**
> Thanks very much for your help everyone. So if I decide to run DBAN before I install Ubuntu, it would go:

Step 1: Run DBAN from boot disc
Step 2: ?????
Step 3: Run Ubuntu from boot disc

Is there a step 2?

Hi, I would really appreciate an answer to this question before I run DBAN?

---

### Post by t0p on 2008-09-20
I don't think there's an intermediate step.  You'll use the ubuntu to repartition the hard drive after dban has nuked the old data.

---

### Post by lazyart on 2008-09-20
Just put in the CD and install ubuntu.  Once you repartition it's not going to try to use or access any of the Vista data.  All the wiping is overkill unless there is data previously on the disk that under no circumstances you don't want ever to be recovered by the FBI, CIA, etc.....

---

### Post by ealrgrey on 2008-09-20
Okay thanks a lot.

---

### Post by mkvnmtr on 2008-09-20
On my Mac I use Drive Genius to shred the unused parts of the partition. It will also do the whole disk. It does a lot of other things also. I am sure there is a version for Windows. It will not see Linux so you don't want to use it after you have a Linux install. I think there may be programs in Ubuntu to do the same thing but I am not sure. It takes some time to shred and you may want to do it twice just to be sure.

---

### Post by wpshooter on 2008-09-20
> **ealrgrey said:**
> Okay thanks a lot.

Ealrgrey:

You probably don't need to use DBAN.  It is VERY time comsuming and is probably overkill for what you are trying to accomplish.

Get [www.killdisk.com](www.killdisk.com) and WIPE the hard drive completely clean.  This is much faster than trying to use DBAN.  But, of course, it is not as good from a security standpoint.  But unless you are going to be getting rid of your computer (i.e. it is going to be going into someone elses hands, then you probably do not need an absolute secure wiping).

One of the installation processes of installing the Ubuntu O/S is to format your hard drive into various partitions for holding your Ubuntu O/S and other data.  You may want to do some research into how your partitions need to be setup if you are not familiar with this.  One of the main things is to make sure that you make a SEPARATE /home partition.

Good luck.

---

