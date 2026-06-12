---
title: "Unreate USB creator - windows won't recognise"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-07-10
I have a 32 GB drive with a USB cable.

I backed up to it from my Linux. I also backed up the USB Creator.

Now the whole 32 GB drive has decided it IS linux. ie it seems to have created itself and formatted the drive just by me copying it there.

Anyway the problem is now I cannot read it in windows and I cannot "uncreate" it (remove all the linux folders and formatting it created) so that it is just my backup drive.

Any help greatly appreciated.

---

### Post by darksidedude on 2012-07-10
if you want to be able to read ext2 3 or 4 in windows use Ext2read, found it here[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html]("http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html")

if you want to reformat it and start over you can use computer management in windows to reformat it, or use Disk utility in lubuntu.

---

### Post by zwygart on 2012-07-10
How do you backed up? Wich software or command did you use? 

May be it's a partition problem : pleaes post the output of the following commands (and your drive plugged in). 

sudo fdisk -l 
sudo blkid

This will help see what happened and how to help. 
If the drive really is formatted, then try just reformat it with the right filesystem on it.

---

### Post by Bucky Ball on 2012-07-10
> **darksidedude said:**
> if you want to be able to read ext2 3 or 4 in windows use Ext2read, found it here[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)



This is **not** for EXT4 partitions. It can seriously screw them. Read the posts down the link. 

Reading EXT* from Windows is a frustrating adventure, bravely undertaken, though apparently it can be done; a tree-sprite in the woods once told me ... ;)

Hopefully someone knows the spell to help you out ... Good luck ...

PS: Sounds to me like you've either installed Ubuntu to the USB, creating a persistent boot; done what USB creator is intended for: Creating Ubuntu install USBs (Are you sure your personal data is still on there?) or, third option; you formatted the USB as an EXT partition without realising Win can't deal with them, then copied your personal data over.

From your original post it's not real clear which path you've taken, sorry ... ;) Any chance of letting us know what you did leading up to this, in detail???

---

### Post by Kevin McCready on 2012-07-10
thanks for the suggestions. output of fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00080308

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968687615   484342784   83  Linux
/dev/sda2       968689662   976771071     4040705    5  Extended
/dev/sda5       968689664   976771071     4040704   82  Linux swap / Solaris

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eda3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   115656703    57827328   83  Linux
/dev/sdc2       115658750   117209087      775169    5  Extended
/dev/sdc5       115658752   117209087      775168   82  Linux swap / Solaris

output of blkid
/dev/sda1: UUID="bd6c2930-ce70-4f34-b4ae-102a5261d837" TYPE="ext4" 
/dev/sda5: UUID="46262ac8-eede-4442-83c0-41ea18bb0487" TYPE="swap" 
/dev/sdc1: UUID="a42b23cd-d660-4b1a-b910-f6813a281cea" TYPE="ext4" 
/dev/sdc5: UUID="e760f809-a8be-493c-8177-0b93429c9c1b" TYPE="swap" 

I don't want to wipe out the data I already have there. Which linux has put in a home folder on the drive. And I'm not sure how to do it anyway if windows doesn't recognise it.

---

### Post by Kevin McCready on 2012-07-10
Thanks again, esp for warning on danger. re
"PS: Sounds to me like you've either installed Ubuntu to the USB, creating a persistent boot; but probably you have done what USB creator is intended for: Creating Ubuntu install USB. Are you sure your personal data is still on there? Third option; you formatted the USB as an EXT partition without realising Win can't deal with them, then copied your personal data over."

My data is definitely still there in a folder which has named itself:
/media/a42b23cd-d660-4b1a-b910-f6813a281cea/home/k/Documents/

I didn't format. It's a very old hard drive going back a long way with data from the 1990s. I bought a little black box in the late 90s with some USB electronics in it, in which I put the harddrive from an old laptop. My guess is that the USB Creator has decided to do it all by itself when I switched to linux a while ago - bugger!

Sorry I forgot to answer the other question. I don't use a backup program. I just copy and paste from my data folder.

---

### Post by zwygart on 2012-07-10
Strange. You talk about Windows, but I don't see windows partitions. Did you removed some parts of the output or did you used another computer? It's not a LiveCD since LiveCD's didn't have swap.

Also you talked about a 32G Drive, but the one shown my fdisk has 60G.

Since you have Linux, you just have to copy the data you want to your Linux, format the disk with gparted and reput the datas. 

There are no other recommended ways if you want to access this drive with Windows. Format it to FAT32 or NTFS.

---

### Post by Kevin McCready on 2012-07-10
I tried to use my wife's computer which is windows7. Oops I made a mistake on the size of the drive. It is 60GB but Dolphin on my linux reports it as 55.1

---

### Post by zwygart on 2012-07-11
As you can see, there is also a swap partition on your drive, which is completely useless and uses 775Mo. 

If you don't wan't format, you may just delete the other folders on the drive, since you don't use it. 

It depends on you if you want to be able to access it at any cost. Note that at "anytime" you will be able to boot with a LiveCD and copy/paste data into a Windows machine if some bad should happen.

---

### Post by Bucky Ball on 2012-07-11
Hmmm, mighty odd, as /Documents should be in /home/username/Documents. You look to have two installs, maybe one on USB, one on hard drive. Looks like one install is mounting the other's /home partition in its /media directory under /media/a42b23cd-d660-4b1a-b910-f6813a281cea/home/k/Documents/, where the alpha-numeric is possibly the UUID of the drive/USB.

Are you booted into one install and looking at the /home partition of the other? Presuming 'k' is your username?

---

### Post by Kevin McCready on 2012-07-11
I'm using Dolphin to view. And yes the problem seems to be 2 installs. The one on my computer may be mounting the one, if it is one, on the 60GB USB. Yes re k.

---

### Post by Bucky Ball on 2012-07-11
So, think that is your problem. Which device do you want to be running Ubuntu from? Delete the other using Gparted (you need to unmount the partitions in Gparted by right clicking to do this) BUT, you need to make sure which install you are booting from (which one's grub is installed to the MBR) as if you delete that one you won't be able to boot.

---

