---
title: "Additional hard drive"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by chkneater on 2008-11-27
I just installed a hard drive that has Xubuntu installed on it.  I jumpered it to be a slave drive for my HD which is full.  I am running 8.04 and cannot see that additional hard drive anywhere.  Should I jumper it differently or is there a certain way to mount it? Thanx in advance!!

---

### Post by drs305 on 2008-11-27
Run this and post the results:
```
sudo fdisk -l
```

It will show the device if linux sees it.

---

### Post by chkneater on 2008-11-27
This is what I got with that command.  It doesn't even seem to recognize the new drive?!


Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82

---

### Post by taurus on 2008-11-27
Reboot your machine and go into the BIOS and see if the BIOS even detects the second harddrive.

---

### Post by chkneater on 2008-11-28
WEEELLLLL,,, after a reboot the system recognizes it, BUT ( they should name UBuuuutU!) it will not grant me permission to mount it.  It shows up under Places/computer but my password will not work when I try to change the permissions.  Might it not have been unmounted right?  I've never had to mount or unmount a hard drive with ubuntu?  HMMmmmm....  Wish I could just go into a terminal and sudo it and just have it work!!  Even if I got the order wrong on the IDE cables, then that drive would have booted instead, right?  This is really weird.  I want to install 8.1 on it and keep 8.04 as my Just In Case!  Thanx for the help.  Just don't know how let it grant me the permission to access it.

---

### Post by chkneater on 2008-11-28
Seriously Taurus, how did you get those golden beans?!  That's awesome!

---

### Post by Elfy on 2008-11-28
> I want to install 8.1 on it and keep 8.04 as my Just In Case! Thanx for the help. Just don't know how let it grant me the permission to access it.

If that's what you want to do - boot with the livecd - when you reach the partition part, tell the installer to use the whole of the second disk - make sure you don't pick the one with 8.04 - and it will format the 'new' disk, make the partitions and install.

You will then find that 8.04 will be added to the 8.10 menu list so that you can boot either.

---

### Post by chkneater on 2008-11-28
Allright, I'll give that a try then.

---

### Post by chkneater on 2008-11-29
That worked and bptj hard drives are working and have OS's on them and I can dual boot just fine, BUT when trying to read file from the 8.10 drive on while logged onto the 8.04 drive I still don't have permisions to,  I can move files back and forthe froom the 8.1 drive just fine tho?

---

