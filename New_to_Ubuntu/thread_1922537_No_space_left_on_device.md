---
title: "No space left on device"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by zulasmum on 2012-02-09
I have just set up a headless server using 10.04 but seem to have set up the partitions incorrectly and have no space left to copy files onto my server.
I know the disk has loads of space as it is 320gb
Any advice on how to change the relevant partition.
Thanks

---

### Post by sikander3786 on 2012-02-09
Please post the output of these commands to let us see your current partitioning setup:

```
sudo fdisk -l
df -h
cat /etc/fstab
```

If you've lost space on your '/' partition, there isn't much you can do besides re-installing, I fear. However, you might be able to backup your current install and extract it to a new partition, a bigger one.

If you have got space on your '/' and that isn't causing a problem and as you said, you've got some free space on the HDD, the problem is probably that either you left the remaining space 'unallocated', or even if you created a data partition there, you didn't chose to mount it under Ubuntu. If that is the case, the solution is much easier.

The outputs will help us know more about your problem.

---

### Post by Bucky Ball on 2012-02-09
> **sikander3786 said:**
> If you've lost space on your '/' partition, there isn't much you can do besides re-installing, I fear. 

? That would be the last option. What's the matter with booting from the LiveCD, running Gparted, shrinking the partition next to / and expanding / into the free space created???

---

### Post by sikander3786 on 2012-02-09
> **Bucky Ball said:**
> ? That would be the last option. What's the matter with booting from the LiveCD, running Gparted, shrinking the partition next to / and expanding / into the free space created???
Hmmm. I wasn't ever successful with partition resizing. But that obviously doesn't mean that no one else can be successful with it. I should have listed that option as well.

However, For the OP, I still strongly believe that the free space isn't mounted under Ubuntu and the solution would be simple.

---

### Post by Paqman on 2012-02-09
> **Bucky Ball said:**
> ? That would be the last option. What's the matter with booting from the LiveCD, running Gparted, shrinking the partition next to / and expanding / into the free space created???

^ This.

In the meantime if you need some space to work with, you can create some space immediately by cleaning out your APT cache and removing extraneous packages:
```
sudo apt-get autoremove && sudo apt-get clean
```

---

### Post by zulasmum on 2012-02-09
The output of **fdisk -l** is:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cf99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       38914   312320001    5  Extended
/dev/sda5              32       38914   312320000   8e  Linux LVM

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

The output of **df -h** is:


Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/server1-root
                       22G   22G     0 100% /
none                  998M  240K  998M   1% /dev
none                 1002M     0 1002M   0% /dev/shm
none                 1002M  424K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw
none                   22G   22G     0 100% /var/lib/ureadahead/debugfs
/dev/sda1             228M   31M  185M  15% /boot
/dev/sdb1             296G   71G  211G  26% /media/backupdrive

The output of **/etc/fstab** is:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/server1-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=9af211cd-95b5-4e80-94b4-96c70638dbe8 /boot           ext2    defaults        0       2
/dev/mapper/server1-swap_1 none            swap    sw              0       0
/dev/sdb1 /media/backupdrive ext3 defaults 0 0

---

### Post by zulasmum on 2012-02-09
I should say that I have 2 drives of 320GB. One is just a back up drive, sdb1, I believe.

---

### Post by Bucky Ball on 2012-02-09
Simpler is:

```
sudo blkid
```That will show all physical drives, all partitions, names, etc ...

---

### Post by zulasmum on 2012-02-09
The output of blkid is:

/dev/sda1: UUID="9af211cd-95b5-4e80-94b4-96c70638dbe8" TYPE="ext2"
/dev/sda5: UUID="0k3bdV-dqzl-oFwU-8SGH-AVNd-XBW9-Mg0Fzh" TYPE="LVM2_member"
/dev/sdb1: UUID="d1adc9af-6592-4c32-a2db-c1463bb00291" TYPE="ext3"
/dev/mapper/server1-root: UUID="426e7ee8-b237-485a-b852-43b999d8fa1d" TYPE="ext4"
/dev/mapper/server1-swap_1: UUID="9838ac58-15e6-4a56-bac7-ce454139ff1a" TYPE="swap"

---

### Post by Bucky Ball on 2012-02-09
Okay, that seems like a rather strange setup. You have EXT2, 3, and 4 partitions. How did that happen? Which one is your current Ubuntu (the headless server install)? What's one these other partitions? Also not sure about these two entries:

```
/dev/mapper/server1-root: UUID="426e7ee8-b237-485a-b852-43b999d8fa1d" TYPE="ext4"
/dev/mapper/server1-swap_1: UUID="9838ac58-15e6-4a56-bac7-ce454139ff1a" TYPE="swap"
```But could be a server convention and lingo I am not familiar with. Where, physically, is /swap exactly?

---

### Post by zulasmum on 2012-02-09
re the mixed partitions - not sure if it was because I installed 10.04 on a drive that had 8.04
I can't answer the question about the last 2 lines, only that server1 is the name I gave to my server as I installed it.

---

### Post by zulasmum on 2012-02-09
Sounds like it may be easier to start afresh and do a clean install?

---

### Post by Bucky Ball on 2012-02-09
> **zulasmum said:**
> Sounds like it may be easier to start afresh and do a clean install?

Hmm. Might be if you've just started on this and have back-ups of anything you need. I would get rid of the lot and start from scratch if possible. 10.04 LTS server edition is supported until April 2015 so you are going in the right direction there. LTS releases definitely advised for servers and other production machines. ;)

* Just did a bit of research and /dev/mapper seems to be connected with RAID or fakeRAID. Have you experimented with RAID? It may, as I say, just be server things that are quite normal. Maybe someone else can throw some light ...

---

### Post by zulasmum on 2012-02-09
Thanks for your help, Bucky Ball. I have back ups so am going to start again.

---

### Post by SeijiSensei on 2012-02-09
The /dev/mapper entries reflect the fact that he is using LVM.  Unless you really know what you're doing, I'd dump LVM and stick to ordinary partitions.  

With two disks, RAID1 might be another good idea.  If you allocate equal-sized partitions on each disk and mark them as partition type "fd" (or Linux RAID), you can then create a RAID1 array on each pair of partitions using mdadm.  I'd then mount them as /var and /home since those two directories get the most activity.

---

### Post by zulasmum on 2012-02-09
The LVM partitions are the default settings when installing. Should I then go with "Guided - use entire disk" instead of "Guided - use entire disk and set up LVM"?

---

### Post by SeijiSensei on 2012-02-09
I don't recall that being the case the last time I installed 10.04 Server.  

(Edit: I just ran the 11.10 Server installer, and you're right that it offers LVM as the default option.  I'd pick either "Guided - Use Entire Disk" or "Manual."  LVM has some nice features like on-the-fly resizing and the ability to make a "snapshot" of a virtual partition, but it's way overkill for inexperienced users.)

I always partition the drives manually and eschew the "guided" options.  In some cases I'll run the Live CD and use fdisk from the Terminal to create the partitions beforehand, then reboot and run the installer and tell it how to use the pre-existing partitions.

If this is your first time with an Ubuntu server, I'd just use the "guided - entire disk" option unless you have other partitions on the drive that contain data you need to keep.  In that case, you'll need to partition manually.

---

### Post by Bucky Ball on 2012-02-09
Manual partitioning for me. That way you can create a separate /home partition, which some don't but I always do. ;)

---

