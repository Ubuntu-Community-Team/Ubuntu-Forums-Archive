---
title: "Advice on Partitioning"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Victoriousness on 2012-05-15
Hi all, I'm completely new to Linux, and I'm trying to install Ubuntu onto my laptop which is running Win XP. I want to dual boot, and I currently have my drive partitioned into C: (67.4GB) and D: (12.6GB). I want to install Ubuntu on the D drive, but when I go into the installer, it only lets me choose to split up my C drive. Is there an easy way to just install Ubuntu on the D and not change anything on C?

I'm trying to avoid making the swap partition and then another one with double my RAM, etc. That stuff confuses the hell out of me.

---

### Post by Lisiano on 2012-05-15
Do you wish to replace D or are you planing to intall it on D as in without formating it?

---

### Post by Victoriousness on 2012-05-15
There's nothing on D right now, so I can definitely format it.

---

### Post by DogMatix on 2012-05-15
You could install ubuntu on D: and boot to it via BIOS.

EDIT: Ah! Its a partition not a separate HDD, sorry.

---

### Post by Lisiano on 2012-05-15
When installing Ubuntu, select Something Else (Or whatever is the last option is called), pick the smaller partition in the list, press Edit, tick Format, use as: EXT4 and make it so the text in the lowest box is / (Yes, just a slash), then continue the install.

---

### Post by Victoriousness on 2012-05-15
Ok, thanks. That makes perfect sense. Should I select D as the device for boot loader installation too?

---

### Post by Lisiano on 2012-05-15
No, for that you wish to use sda, or the disk as a whole, the only options you should see (If you are telling us everything) is sda, sda1 (Which should be C) and sda2 (Which should be D).

---

### Post by SeijiSensei on 2012-05-15
Just to be clear, Linux doesn't use the drive letter method that Windows does.  Partitions are referenced either by something like /dev/sda2 or by the partition's unique identifier called a UUID.  The first hard drive is called /dev/sda, and the partitions are numbered in sequence starting with one.  So "drive C" will be /dev/sda1 and "drive D" will be /dev/sda2.

So during installation, when you get to the partitioning step, choose "manual", then select the /dev/sda2 entry and tell the installer to format it with ext4 and mount it as "/".  You'll also need to install the boot loader called GRUB in the "master boot record" of /dev/sda.  When the installer is finished and you reboot, you should be presented with a menu that offers you the choice to boot with Ubuntu or Windows.

---

### Post by Lisiano on 2012-05-15
> **SeijiSensei said:**
> So "drive C" will be /dev/sda1 and "drive D" will be /dev/sda2.I must disagree, Windows sequentially assigns letters so his drive D can be sdb1 or sdc1. Also Windows let's users reassign letters to drives as they see fit so I can have my "D" on "Y" yet in Linux it's sda2.

/rant

---

### Post by westie457 on 2012-05-15
@ Victoriousness

The advice given by the others is good however there might be a recovery partition on your hard drive that is hidden. So just to make sure that all is okay could you boot into a Live Desktop (CD/USB) in 'Try' mode. Open a terminal by pressing Ctrl+Alt+T and run ```
sudo fdisk -l
```
The l is a lowercase L not a 1. Post there output back here.


EDIT If you have a hidden partition the numbering will need changing because you will have 3 partitions listed not 2

---

### Post by Lisiano on 2012-05-15
Win XP didn't usually come with recovery partitions I think, but if it does exist, then you shouldn't touch it as long as you wish to keep using XP. While removing it will not destroy XP, it will stop you from being able to restore it to factory defaults.

---

### Post by DingusFett on 2012-05-15
Most laptops come with a hidden recovery partition instead of giving you disks for if you need to wipe it to start from scratch. My old Acer laptop from years ago that came with XP had one.

---

### Post by Victoriousness on 2012-05-15
I'm not sure about the whole recovery partition thing, but I went ahead and installed Ubuntu. It's up and running, but now I need to figure out how to get my wireless working. Anyway, that's a topic for another post. Thanks for all the help guys!!!

---

### Post by Lisiano on 2012-05-16
Please mark the thread as solved (Top of the page -> Thread tools) and leave a link to the new thread so we can find it faster

---

