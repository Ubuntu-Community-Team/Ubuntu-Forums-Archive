---
title: "Cant boot HP_RECOVERY"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by System Monitor on 2008-10-02
For some reason my hp recovery drive will not boot, and I would like to install vista again because I cant get my built in microphone working. When I try to boot into the hp recovery drive i get a black screen and it doesn't change, what can I do to get it working?

---

### Post by Nano Geek on 2008-10-03
I'm not sure if it would work, but you could try using the Vista DVD that came with the laptop and see if that will let you restore Vista.

---

### Post by Nepherte on 2008-10-03
Nowadays manufacturers don't deliver any dvds anymore, solely recovery disks which you can burn yourself. Does it give any error when you try to boot into the recovery partition?

---

### Post by mike555 on 2008-10-03
If you formatted your harddrive for Ubuntu it won't see it ...... if you have a ntfs partition it should ...

---

### Post by lisati on 2008-10-03
I had a similar problem yesterday on a Compaq machine (they're made by HP) - the partitioner experienced problems when I was trying to install a dual-boot Xubuntu - and I ended up with being able to boot XP, but not directly from the recovery partition by pressing F10 on startup (as it should) and gparted on the LiveCD was unable to "see" the partitions. After several hours mucking about (muttering and cursing about my ignorance in the process) I was able to get the LiveCD to see the partitions. 
One thing I noticed a few minutes before hitting on a solution was that running fdisk -l from the terminal produced a warning about the recovery partition having an invalid flag. I adapted a solution for a similar problem (found [here]("http://ubuntuforums.org/showthread.php?t=889843")). Although I still wasn't able to use the F10-at-boot method to start up the recovery process, I was able to get XP bootable fairly quickly (its partition was still there, thankfully)  and I restarted the recovery process from the Compaq software wizard, which also fixed up the F10 method.

If you don't have the original Windows parition but Ubuntu is able to see the recovery partition, one option to check out might be to burn a copy of the recovery partion onto a bootable CD or DVD. 

Hope this gives you a couple of ideas that help save you some time.

p.s. Don't be fooled by my post count - I'm still a bit of a bumbling boob compared to many of the other forum members when it comes to doing some things.

---

### Post by System Monitor on 2008-10-03
I dont get any error and this is what i get for fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066a6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25496   204792868+  83  Linux
/dev/sda2   *       25497       29320    30716280   af  Unknown
/dev/sda3           29321       30401     8683132+   7  HPFS/NTFS

```

---

### Post by lisati on 2008-10-04
> **System Monitor said:**
> I dont get any error and this is what i get for fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066a6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25496   204792868+  83  Linux
/dev/sda2   *       25497       29320    30716280   af  Unknown
/dev/sda3           29321       30401     8683132+   7  HPFS/NTFS

```

Hmmmm... I'm just thinking aloud here without necessarily having a solution. On my Compaq machine, the recovery partition (drive D: within windows) shows up on fdisk as /dev/sda1 with a fat32 file system, my XP partition is /dev/sda2 (C drive, uses NTFS) and my Linux partition(S) as ext3 etc......perhaps the recovery system on your machine is expecting its partition to be the first on your disk.

---

