---
title: "Removing one distro (opensuse) and keeping ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by hermitical on 2008-04-28
I have Ubuntu and Opensuse on my laptop (inadvertently ditched Vista!)
Opensuse was installed before ubuntu
Looking at G-part I have 4 partitions
/dev/sda1 - linuxswap
/dev/sda2 - ext3 /media/sda2 boot
/dev/sda4 - ext4
/dev/sda3 - ext3 /media/sda3

sda3 has all my media (music, video etc) sda2 is my opensuse partition and is flagged as boot but I want to get rid of it. Am I ok to go ahead and delete then resize or should I do something else first?

---

### Post by bluefrog on 2008-04-28
you can do as you wish as long as you don't touch sda3 which contains your data.
if you have anything in your home folder you want to keep, copy it to sda3.

---

### Post by bodhi.zazen on 2008-04-28
You should be just fine deleting and resizing the partition.

You will need to set one partition as bootable, does not matter to linux which one.

---

### Post by Oldsoldier2003 on 2008-04-28
> **hermitical said:**
> I have Ubuntu and Opensuse on my laptop (inadvertently ditched Vista!)
Opensuse was installed before ubuntu
Looking at G-part I have 4 partitions
/dev/sda1 - linuxswap
/dev/sda2 - ext3 /media/sda2 boot
/dev/sda4 - ext4
/dev/sda3 - ext3 /media/sda3

sda3 has all my media (music, video etc) sda2 is my opensuse partition and is flagged as boot but I want to get rid of it. Am I ok to go ahead and delete then resize or should I do something else first?

If your Ubuntu was installed after OpenSuse then (unless you messed with it Ubuntu's grub installation and /boot/grub/menu.lst is the active one.) you should be able to remove the suse partition and resize without any issues. I would keep a live CD or a [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") available just in case something you do in your partitioning messes up grub.

The easiest and safest way would just be to wipe out Suse and use the partition as a data partition. Just add it to your fstab and use it for storage ;) if you do that your partitions wont change and you wont even need to update grub, you can just delete the suse options from menu.lst

---

### Post by hermitical on 2008-04-28
there only seems to be an option for unmounting it?

---

### Post by Oldsoldier2003 on 2008-04-28
You have to unmount a partition before you can do any partitioning operations on it. (or boot from a live cd)

If you are booted in ubuntu you should be able to work on your suse partiton with gparted.

---

### Post by bodhi.zazen on 2008-04-28
In gparted  I assume ???

You need to run gparted from a live CD and yes you need to umnount a partition before you can manage it (delete / resize / format).

---

### Post by hermitical on 2008-04-28
is there a maximum size for a partition? can't seem to resize it any larger than it is

managed to delete the opensuse partition thoug.... cheers!

---

### Post by bodhi.zazen on 2008-04-28
No, the problem is you need to have the free space adjacent to the partition you want to add to.

You may need to add space to you logical partition first. You may need to move partitions.

---

### Post by hermitical on 2008-04-29
not managed that yet but now I have another problem. On booting I get to a point with a whole page of script including this:


I've had a quick look and it seems it might be something to do with Grub. I used the /etc/fstab/ command and got this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=eab0c493-03ea-4f5f-b620-556b4ddcd774 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=97aff8fb-648a-4aae-b711-33f5cc52c4b3 /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=7a19672e-95fe-4166-95b5-9f7c00458dd4 /media/sda3     ext3    defaults        0       2
# /dev/sda1
UUID=1d9e479c-e3fa-47c5-ab4f-074a80f7b7fb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I read that the UUID might be different and need changing (remarking?) so I checked the UUID of /dev/sda4 using sudo /sbin/vol_id -u /dev/sda4 but it got the same result.

I can get through that initial page using ctrl-d but I'd like it not to be there!

---

### Post by hermitical on 2008-04-30
here's the fsck log entry:

Wed Apr 30 11:30:37 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=97aff8fb-648a-4aae-b711-33f5cc52c4b3'

/dev/sda3: clean, 28490/16662528 files, 29993751/33302745 blocks
fsck died with exit status 8

---

### Post by A$h X on 2008-04-30
I have similar question:

I have ubuntu and xubuntu installations on separate partitions. Xubuntu was installed last, so grub points to it's menu.lst. Say I wanted to delete the xubuntu partition (using gparted), would I need to modify grub in anyway, or would it point to the currently redundant menu.lst on my ubuntu partition?

---

### Post by bodhi.zazen on 2008-04-30
> **A$h X said:**
> I have similar question:

I have ubuntu and xubuntu installations on separate partitions. Xubuntu was installed last, so grub points to it's menu.lst. Say I wanted to delete the xubuntu partition (using gparted), would I need to modify grub in anyway, or would it point to the currently redundant menu.lst on my ubuntu partition?

You will need to re-configure grub.

See these links :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

