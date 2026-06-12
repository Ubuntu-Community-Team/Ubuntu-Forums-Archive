---
title: "Allocate unallocated space"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Dave2081 on 2008-08-28
another partitioning question
here are two images of whats going on
[http://www.daveelliottonline.com/unallocatedDrive.html](http://www.daveelliottonline.com/unallocatedDrive.html)
I partitioned my swap drive to be way to big when I first installed ubuntu, then I decided to shrink it down. Which all that went pretty well, except now I can't re-merge that 21 GiB, with my vista partition which is where I want it. Can I do this from vista or do I do it from gparted?
thanks in advance,
dave:lolflag:

---

### Post by RolandFlagg on 2008-08-28
lol did you initially make your swap bigger than your ext?
I'm not sure how exactly you would be able to fix the problem, but I know for sure that unless you have PMagic, you probably can't do anything about it under windows. The built-in partition program can't resize or move. My best bet would be tinckering with gParted, see what you can do with the "resize/move" option.

---

### Post by bodhi.zazen on 2008-08-28
You can only have 4 primary partitions.

So your options are to resize one of your existing partitions and add the unallocated space to it, or delete 1 of your primary partitions and make an extended partition.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

To manage your partitions, use gparted from the Ubuntu desktop CD :

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Dave2081 on 2008-08-28
I'm downloading pmagic now. I messed around with Gparted for an hour before and it just wouldn't move close to the vista partition. It has to be next to it to merge it or something, but I couldn't move it. Any other utilities or program suggestions would be great though, I'll try out this one and hope it works. Oh initially both the ext and swap were huge, but then I shrunk both.

---

### Post by jbrown96 on 2008-08-28
This is a little difficult because of the restriction on the number of partitions. You cannot have more than 4 partitions at a time, so you will have to juggle them around a bit.

Here's what you will need to do.
1. Boot up the LiveCD
2. Open the partition editor (System-->Administrator)
3. delete the swap partition
4. Create a new Ext3 partition with the unallocated spaced near the end of the drive (right before your recovery partition). When you create this, create it at the end of the space. Make it the same size as your current Ext3 partition (doesn't have to be, just makes it easier)
5. Create swap space (I'm guessing you want to stick with the ~3GB) at the end of the space just before your new Ext3 partition. 
6. Mount the two ext3 partitions and copy data. Check out the partition numbers (/dev/sda1, /dev/sda2, etc) so you know which is the new Ext3 and the old Ext3.
```
sudo mkdir /media/old /media/new
``` ```
sudo mount -t auto /dev/sdaY /media/old
``` ```
sudo mount -t auto /dev/sdaX /media/new
``` Obviously make sure that you replace Y and X with the appropriate partitions. ```
sudo cp -R /media/old /media/new
```
7. correct the boot status.
I'm not sure how you were booting into Ubuntu since you're Windows partition is marked as bootable. If you are using grub you will need to update the partition number in it. Otherwise, fix whatever boot utility you use.
8. resize Vista
I would delete the Ext3 partition in Gparted (Partition Editor) and then expand the NTFS partition in Windows (NTFS is proprietary so it's riskier using a non-windows system to manipulate NTFS).

---

### Post by RolandFlagg on 2008-08-28
sounds like you just installed ubuntu. You know, I had the same problem a couple of weeks ago, and I couldn't figure out how to merge the partitions either (actually I needed 2 partitions for windows, so my equivalent of yours is to make the current "unallocated" space a different partition).
It's always good to have two partitions under windows, since that way its like both windows and ubuntu are sharing it. Since you can't make more than 4 partitions, I ended up deleting ubuntu (since I just installed it anyway), so there are just 2 partitions, the windows partition and the factory recovery console. Then I make an extended partition that extends C:. Finally I installed ubuntu again with a swap. Now everything works perfectly.
I just thought that doing an altogether reinstall of ubuntu is faster than trying to figure out and then change the partitions, plus pmagic costs money too XD

---

### Post by Dave2081 on 2008-08-28
bodhi.zazen,
I don't have a ubuntu CD, I can't just do this from inside Ubuntu? I think theres a ubuntu CD at a electronics recycling place down the street though, so I could easily go get one.

---

### Post by RolandFlagg on 2008-08-28
yea you need a ubuntu cd, because when you edit the stuff INSIDE ubuntu... I think it would screw up everything, since when you are in ubuntu, you are using the swap...

---

### Post by jbrown96 on 2008-08-28
You may be able to do it without a livecd. Be warned that this could be very unstable. You will need to have at the very minimum 512MB (I wouldn't try with less than 1GB) of Ram. When GRub starts hit "Esc" to get to the menu. Press "e" and then go to the second line and press "e" again. At the end of the line type "single" (no quotes), press enter and then "b". Follow these instructions > 2.3. Removing Swap Space
 To remove a swap partition: 
The hard drive can not be in use (partitions can not be mounted, and swap space can not be enabled).
Alternately, if the drive does not contain any partitions in use, you can unmount them and turn off all the swap space on the hard drive with the swapoff command.
At a shell prompt as root, execute the following command to make sure the swap partition is disabled (where /dev/hdb2 is the swap partition):
swapoff /dev/hdb2
Remove its entry from /etc/fstab.
Make sure you change to /dev/hdb2. you can find what is swap with ```
fdisk -l
``` Remove it from Fstab ```
vi /etc/fstab
``` use the arrows to scroll to the line that has your swap entry. Press "dd" to delete the line. "Esc" then ":x" (damn smiley it should be ": x" with no space) to save and exit. reboot and do the "single" thing again. Remove the swap partition with ```
parted remove /dev/sdaY
``` (use fdisk -l to find the partition DO NOT MAKE A MISTAKE HERE). Try to reboot as normal and get into Gparted and follow my instructions from there. 

Edit: It will be much more complicated to delete the old Ext3 partition. You will need to boot to the new Ext3 to do this. Do you use Grub and how is it configured on Windows?

---

### Post by Dave2081 on 2008-08-28
I think I'm just going to download the ubuntu live cd disk image and burn it to a cd, and then do the gparted thing. that should work right?

---

### Post by bodhi.zazen on 2008-08-28
> **Dave2081 said:**
> I think I'm just going to download the ubuntu live cd disk image and burn it to a cd, and then do the gparted thing. that should work right?

Yes, in general you need a live CD. You may be able to do it with a pivot root, but it is more complex that way ...

Next, you need to move your partitions so the unallocated space is adjacent to the partition you wish to enlarge. You will need to do this in multiple steps, make a change, and then implement it, then make another change.

---

### Post by jbrown96 on 2008-08-28
Should work fine. Could you explain how your system boots. Did you install Grub in Windows??? That could be the only problem

---

