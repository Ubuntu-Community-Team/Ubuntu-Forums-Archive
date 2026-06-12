---
title: "How to unistall Ubuntu"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by new123 on 2011-09-28
First I had Win XP and now I installed Ubuntu and got them both, I can select which one to start on boot, but I want to uninstall Ubuntu (and GNU GRUB if possible), I had some problem on Ubuntu only with startup so I gave up trying.
I got 80 GBs of total HD space (20 for Ubuntu, 60 for Win) and also, when I uninstall Ubuntu, I want to back those 20 gigs to Windows... How?

---

### Post by Immolatus on 2011-09-28
use the windows disk/ rescue partition(whichever came with your computer). The system rescue utility can remove grub and put widows back in control of the MBR. Then just resize the partition from within windows.

---

### Post by ajgreeny on 2011-09-28
Make sure you fully backup as many CDs that come with machines now are just to restore the disk to the same state that it was when you first got it, and in many cases are not "rescue" disks but "restore" disks.

An alternative method is by doing the following from your Live Ubuntu CD/USB:
```
sudo apt-get install lilo
```
Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again and grub will be gone.

Having checked that you can now boot directly into windows you can use Gparted on the live ubuntu CD and delete the Ubuntu partition and either stretch the XP partition to fill the space, or format the space as ntfs and keep it as a seperate partition.

---

### Post by new123 on 2011-09-28
> **ajgreeny said:**
> Make sure you fully backup as many CDs that come with machines now are just to restore the disk to the same state that it was when you first got it, and in many cases are not "rescue" disks but "restore" disks.

An alternative method is by doing the following from your Live Ubuntu CD/USB:
```
sudo apt-get install lilo
```Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```Then you should be able to boot directly into Windows again and grub will be gone.

Having checked that you can now boot directly into windows you can use Gparted on the live ubuntu CD and delete the Ubuntu partition and either stretch the XP partition to fill the space, or format the space as ntfs and keep it as a seperate partition.

I did the alternative method, I typed this 
```
sudo apt-get install lilo
```Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```

but I dont know where precise it Gparted to run it..

---

### Post by ajgreeny on 2011-09-28
Having used those two commands check that your windows XP boots properly without looking for grub first.

Assuming that it does, boot the Live ubuntu CD again and go to System->Administration->Gparted and the program will open showing all your current partitions.  If you're using 11.04 live CD with the unity desktop, click on the icon top left and type **gparted** in the box that appears.

From gparted you can delete the Ubuntu partition which is probably showing as ext4 format, and also the swap partition.  Now either stretch the XP partition or make a new ntfs partition in the free space.

---

### Post by new123 on 2011-09-28
> **ajgreeny said:**
> Having used those two commands check that your windows XP boots properly without looking for grub first.

Assuming that it does, boot the Live ubuntu CD again and go to System->Administration->Gparted and the program will open showing all your current partitions.  If you're using 11.04 live CD with the unity desktop, click on the icon top left and type **gparted** in the box that appears.

From gparted you can delete the Ubuntu partition which is probably showing as ext4 format, and also the swap partition.  Now either stretch the XP partition or make a new ntfs partition in the free space.

Yh Win runs without selecting it, no grub shows up. That means Im on Gparted step, but when i try to delete ext4 I get following msg>  Unable to delete dev/sda6! Please unmount any logical partitions having a number higher then 6.

While on swap partition which I also have to delete, there is disabled option named Delete. I cant run it.

---

### Post by plucky on 2011-09-28
> While on swap partition which I also have to delete, there is disabled option named Delete. I cant run it. 

The Live Cd will mount the swap partition.

Turn swap off and then see if you can now delete the partitions.

Once the partitions have been deleted,you can now grow the XP partition.


Good Luck

---

### Post by new123 on 2011-09-28
Yeah all done :)) thanks alot !! :) ^^

---

### Post by amjjawad on 2011-09-28
> **new123 said:**
> Yeah all done :)) thanks alot !! :) ^^

Well done :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

