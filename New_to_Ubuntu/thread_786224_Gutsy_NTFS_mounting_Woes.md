---
title: "Gutsy NTFS mounting Woes"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by d4ng3r on 2008-05-07
I am currently running an HP laptop dual booted with Ubuntu 7.10 and Windows XP MCE.  Everything was working fine, until this morning I booted into XP to copy something to a friends external HD, that was formatted NTFS, and for some reason Ubuntu wouldn't mount it.  Anyways, while in Windows the computer crashed and I had to hard shut down, and just said forget it and booted back into Ubuntu.  Now the problem is when I booted into Ubuntu, it no longer mounts my Windows partition.  The NTFS config tool said it was because it was in use, so I proceeded to restart again to boot back into Windows to cleanly shut down...lo and behold I get a Blue Screen of Death when restarting, something about a bad hive file, thats not important.  The point is about getting my Data off of it from Ubuntu.  Now when i'm back in Ubuntu I can see the drive in the Computer tab where is lists all the drives, as 102 gb Volume, but when I click it, it says "Cannot Mount Volume  You are not Privileged to Mount this Volume"  the NTFS config tool notes something about force mounting, but I'm not really familiar with it.  Will it further damage my NTFS drive?  I can fix the windows problem, but Im on Study Abroad, far away from my Windows Install Disk that id need to do it, and in the mean time id like to be able to access the data on that drive (or pull it off if something goes wrong)

So all in all I guess the big question is, how can I mount this partition without further messing it up?

And on a slightly related tangent, do you know why it wouldn't mount my buddies external?

Sorry for such a long post, any help is appreciated.

---

### Post by HornedBeast on 2008-05-12
NTFS formatted drives need to be shutdown correctly, I.E. Windows actually being shutdown and external drives not just being yanked out, but actually being "detached" in the correct way.

There is a force option you can add to your fstab file - it COULD damage the drive, but I have had no problems with it so far. For the instructions on how to force mount the drive manually, plug the drive back in and try and open it from "Computer" It will then tell you it can't mount and you could try forcing it. Simply type the command it suggests into a terminal. 

However, as a side note, you may have trouble if the directory you are trying to mount the drive into doesn't exist, so I suggest creating that first (probably something like /media/sda2. You could even create a folder inside your home called "Ext Drive" and mount into that.

Hope that helps a little!

---

### Post by dixelpixel on 2008-06-14
Hi HornedBeast,

I think your last advice, creating a new directory to mount my external HDD might be where I am going wrong. I created a new directory in Home and now I am trying to use the following force mount code in terminal:

mount -t ntfs-3g /dev/sdb1 /home/"name of folder" -o force

Terminal replies that I can only do this in root. I am (as you probably can tell) a complete noob. What do I do next? Is there some command that can change my terminal access to root and then the code will work? I looked around for such commands but had no luck. I will be very grateful for your help.

Many thanks,
--dxp--

---

### Post by ukripper on 2008-06-14
> **dixelpixel said:**
> Hi HornedBeast,

I think your last advice, creating a new directory to mount my external HDD might be where I am going wrong. I created a new directory in Home and now I am trying to use the following force mount code in terminal:

mount -t ntfs-3g /dev/sdb1 /home/"name of folder" -o force

Terminal replies that I can only do this in root. I am (as you probably can tell) a complete noob. What do I do next? Is there some command that can change my terminal access to root and then the code will work? I looked around for such commands but had no luck. I will be very grateful for your help.

Many thanks,
--dxp--

you need```
 sudo 
``` in front of that

> sudo mount -t ntfs-3g /dev/sdb1 /home/"name of folder" -o force

---

### Post by rockerphil on 2008-06-14
sudo mount -t ntfs-3g /dev/sdb1 /home/"name of folder" -o force


just type that in to terminal, it'll ask you for your your sudo password, just use the same password you use to log in (it won't show up as you type it, but it's there)

---

### Post by dixelpixel on 2008-06-14
Thanks,

Solved problem in other thread.

.dix

---

