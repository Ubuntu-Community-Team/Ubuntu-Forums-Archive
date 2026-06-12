---
title: "After Installing Dual Boot"
date: 2015-12-21
forum: New to Ubuntu
---

### Post by Bryan_Walters on 2015-12-21
Have installed ubuntu with Windows and now I want to remove only windows. How should I make it possible. Thanks in advance for your help!

---

### Post by kc1di on 2015-12-21
There are a couple ways to do that.
I would do a complete reinstall of Ubuntu , but you could also use gparted to erase the windows partition and reformat it to ext4 .  Name the partition extra files or something like that and you will be able to access the space from Ubuntu.  if you go that route make sure after you've done the partitioning that you do
```
sudo update-grub
``` to get rid of the Windows entry in the grub menu.

---

### Post by yancek on 2015-12-21
You could simply format the windows partition(s) to a Linux filesystem to use as data which would be the simplest.  If you have any data you want to keep on the windows partition you would have to move it somewhere else first.  Which windows are you currently using and do you use UEFI?.  If you have all the data off the windows partition and your Ubuntu is a new install and you haven't made a lot of changes, a reinstall would probably be easiest.  If you don't have much experience with partitioning, you might take a look at the GParted Manual at the link below as that is the partitioning software used with Ubuntu.

   [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by Rocky_Bennett on 2015-12-23
Using gparted, it seems that it should be real easy to just reformat the sector that you currently use for Windows to be a data sector for Ubuntu. Of course, as has already been mentioned, it is a good idea to save your files first.

---

### Post by Bryan_Walters on 2015-12-28
Hello,

Thanks you so much all!

What if I want to remove ubuntu and want to keep windows only? Is it possible without formatting my computer?

---

### Post by Herdo on 2015-12-28
EDIT:  Scratch that.  Listen to Mark Phelps below!

---

### Post by Mark Phelps on 2015-12-28
> **Herdo said:**
> Do the opposite.  Use the Disk Management tool while in Windows to reformat the Ubuntu sector to NTFS.  Again, backup any data you want to keep from the Ubuntu installation.

Right ... and then, if the machine was using BIOS and MBR, it won't boot anymore!  Why?  Because the dual-boot modified the MBR to point to the Ubuntu partition, which is gone, and hence, the machine will not boot into an OS anymore.

So, BEFORE you do this, be sure to reset the MBR to point to the Windows partition with the boot loader in it.

---

### Post by Herdo on 2015-12-28
> **Mark Phelps said:**
> Right ... and then, if the machine was using BIOS and MBR, it won't boot anymore!  Why?  Because the dual-boot modified the MBR to point to the Ubuntu partition, which is gone, and hence, the machine will not boot into an OS anymore.

So, BEFORE you do this, be sure to reset the MBR to point to the Windows partition with the boot loader in it.


Doh!  You are right.  Hopefully he saw your post before trying anything.  :S

---

### Post by Bryan_Walters on 2015-12-29
> **Mark Phelps said:**
> Right ... and then, if the machine was using BIOS and MBR, it won't boot anymore!  Why?  Because the dual-boot modified the MBR to point to the Ubuntu partition, which is gone, and hence, the machine will not boot into an OS anymore.

So, BEFORE you do this, be sure to reset the MBR to point to the Windows partition with the boot loader in it.

Thanks Mark,

Yes, my machine using MBR. 

I tried as per the instructions you suggested and it worked.

;)

---

