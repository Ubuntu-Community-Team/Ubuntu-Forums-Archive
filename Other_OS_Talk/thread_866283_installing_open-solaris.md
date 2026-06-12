---
title: "installing open-solaris"
date: 2008-07-21
forum: Other OS Talk
---

### Post by dexter.deepak on 2008-07-21
got my sxde dvd days back, but i cant afford to install it bcoz of the primary partition issue...actually i am having only one primary partition as windows and am afraid to create and modify a new partition to primary...i will have to further edit grub after installing.

i will be happy to get some help regarding the solaris install.
i have tried editing grub many a times, but have always failed...i dont know whats going to be the case when i make a new primary partition.
here is my fdisk:
```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ c W95 FAT32 (LBA)
/dev/sda2 2551 19457 135805477+ f W95 Ext'd (LBA)
/dev/sda5 5101 8924 30716248+ b W95 FAT32
/dev/sda6 8925 14023 40957686 7 HPFS/NTFS
/dev/sda7 2551 2672 979902 82 Linux swap / Solaris
/dev/sda8 2673 5100 19502878+ 83 Linux
/dev/sda9 14024 16455 19535008+ 83 Linux     <--i want an install here
/dev/sda10 16456 19457 24113533+ 83 Linux
```

the required partition is mounted as /future, so i think i should also make some big changes in my /etc/fstab.
```
dpak@dpak-server:~$ df -h -T
Filesystem Type Size Used Avail Use% Mounted on
/dev/sda10 ext3 23G 21G 1.1G 96% /
varrun tmpfs 497M 192K 497M 1% /var/run
varlock tmpfs 497M 0 497M 0% /var/lock
udev tmpfs 497M 68K 497M 1% /dev
devshm tmpfs 497M 12K 497M 1% /dev/shm
lrm tmpfs 497M 38M 460M 8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda9 reiserfs 19G 33M 19G 1% /future
/dev/sda1 vfat 20G 14G 6.2G 69% /media/sda1
/dev/sda5 vfat 30G 28G 2.0G 94% /media/sda5
/dev/sda6 fuseblk 40G 37G 2.2G 95% /media/sda6
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon 23G 21G 1.1G 96% /home/dpak/.gvfs
```

i am hoping for some help.thanks.

---

### Post by dexter.deepak on 2008-07-22
i thought many of you would be having solaris on your systems...am i wrong ?

---

### Post by cardinals_fan on 2008-07-22
I **do** have OpenSolaris on my system.  I just requested a free live CD, stuck it in my drive, rebooted, and installed.  No problems.

---

### Post by L815 on 2008-07-22
I tried the Live CD I ordered, only when I tried accessing some setting, my laptp froze, I had to hard shutdown, and then my laptop wouldn't boot for 5 min for some reason.

---

### Post by dexter.deepak on 2008-07-23
> **cardinals_fan said:**
> I **do** have OpenSolaris on my system.  I just requested a free live CD, stuck it in my drive, rebooted, and installed.  No problems.

did you intall it on the same hard disk on which you have ubuntu ?
my problem is that i am havin only 1 primary partition (sda1 - windows installed)...and 1 extended parttion(sda2),and i want to install solaris on one of the logical drives in the extended parttion.
the problm arose bcoz solaris demends a primary parttion....if someone helps me find how to convert a "logical parttion to primary parttion", only then i think i should be able to install solaris.

---

### Post by cardinals_fan on 2008-07-23
> **dexter.deepak said:**
> did you intall it on the same hard disk on which you have ubuntu ?
my problem is that i am havin only 1 primary partition (sda1 - windows installed)...and 1 extended parttion(sda2),and i want to install solaris on one of the logical drives in the extended parttion.
the problm arose bcoz solaris demends a primary parttion....if someone helps me find how to convert a "logical parttion to primary parttion", only then i think i should be able to install solaris.
I've never had any logical partitions.  My Slackware install (now Xubuntu) dual-booted fine with OpenSolaris.

---

