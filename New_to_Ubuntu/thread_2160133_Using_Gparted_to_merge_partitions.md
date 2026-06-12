---
title: "Using Gparted to merge partitions"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by jamesde93 on 2013-07-05
I inherited a laptop about a month ago. The drive has some unused space that I would like to be added to Ubuntu. I'm really not comfortable doing this without some direction.

Ubuntu 12,04 is on sda8. I would like to add sda4 and sda7 to sda8.

Thank you!

---

### Post by mardybear on 2013-07-06
Howdy....

I'm no expert but i've installed a few systems. You have a pretty complicated drive setup for a laptop - looks like dual boot with a Windows OS. If there's an expert in the house please speak up, but i believe Gparted can only add, remove and stretch/shrink paritions, not merge them together. Plus sda4 is not part of your extended partition, so it can't be 'merged'. Prior to tinkering, ensure all critical data is backed up onto other media (usb memory, burned cd/dvd, networked computer).

If it was my system i would attempt the following:

-delete sda7

-stetch/enlarge swap to take up previous space utilized by sda7

-then shrink swap back down to original size by pushing it towards the back of the drive

-stretching sda8 to take advantage of the additional space gained when the swap was pushed towards the back of the drive

In essence, sda7 will be gone, swap will be at the end of the drive and sda8 will be larger. Unless you're willing to delete the sda3 extended partition, which you won't want to do as it will remove your linux install, sda4 will remain as a separate storage drive. If it was me and this is in fact a dual boot computer, i would then change sda4 from an ext3 to NTFS file system so the partition can easily be accessed by both the Windows and Linux operating systems as shared additional storage.

Good luck,

mardybear

---

### Post by fantab on 2013-07-06
The simplest solution will be to Delete partitions 3 to 8 and redo as you want 'em. You won't be able to merge space with Extended partition, even if you can some way, it won't be recommended.

Back up all your DATA and Redo you partitions using Gparted.

Are you Dual-Booting?

---

### Post by mardybear on 2013-07-06
Me thinks deleting partitions 3 through 8 would not be the simplest solution, as it would then require the reinstallation of the OP's existing Ubuntu install.

Please note, deleting partitions will result in data loss.

mardybear

---

### Post by fantab on 2013-07-06
> **mardybear said:**
> Me thinks deleting partitions 3 through 8 would not be the simplest solution, as it would then require the reinstallation of the OP's existing Ubuntu install.

Please note, deleting partitions will result in data loss.

mardybear

Re-installing Ubuntu was understood. That is the simple and clean way to reorganize partitions.

---

### Post by su:bhatta on 2013-07-06
If jamesde93 has a windows partition, he can use EaseUS s/w to organize the HDD, I couldn't find merging option in GParted n used EaseUS to do it in windows. 
In EaseUS u can merge partitions which are side by side, n create new ones... 

step1) Delete/format & Merge partitions 3-8(when u merge, u get the option in easeUS which particular partition to merge with which one & keep which 1, I never lost a bit of my existing 30GB data, by merging)
step2) create new partition(for use in buntu no formatting required, & create NTFS data partition which can be used by both Windows n Buntu) 
step3) reboot with the Ubuntu CD/USB in the system tray, since grub/MBR is gone, Windows will not load by default(IMPORTANT)
step4) install buntu n create new grub

Fresh system with u, enjoy ur dual boot...

maybe this is not what ur a-looking for, but itz just an option...

---

### Post by Impavidus on 2013-07-06
Partitions sda4 and sda7 are empty (they are, right?), so that's easy. Just delete them. The difficulty is that there are other partitions inbetween sda8 and the ones you want to merge.

The swap partition doesn't contain any files, so moving it to the end of the disk is easy. Gparted can directly move partitions, no need to first exand it to the right and then shrink it from the left. You have to deactivate swap before you can move it.

The more complicated part is your sda5. In principle, you can expand sda3 into the unallocated space where sda4 used to be and then move sda5, but this will be a very slow and somewhat risky operation. Make sure you have that partition backed up (and to be sure the others too). Then you can expand sda8 to the right. What kind of partition is sda5? It's ext3, but the default has been ext4 for several years now, so it has been there for quite some time I assume.

Alternatively, back up everything (you should do so anyway), delete partitions sda3-sda8 and make new partitions from scratch. Do everything from a live disk.

---

