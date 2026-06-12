---
title: "Entire hard drive reads as unallocated, still using everything"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Gerafin on 2008-10-26
Mmmkay. I feel really foolish :P but here goes.

Here's an interesting situation I've found myself in. I was using GParted to reformat a partition that was (until recently) being used for Vista. I needed the extra space for Linux, and Vista broke itself, so I decided to make it Ext3 and say goodbye to gaming until I could buy another hard drive. Of course, since I haven't slept in a while, I managed to mess up royally. All I know is that when GParted re-scanned the hard drive, my entire 250 GB hard drive read as "unallocated." Of course, I'm still running Linux, and it seems like all of my files are still there; I'm feverishly backing up important files onto another hard drive, but it's a slow process that will take a while.

sudo fdisk -l returns: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e6ba4ce

   Device Boot      Start         End      Blocks   Id  System


With nothing listed under devices. So, I'm pretty sure my hard drive is completely unallocated as GParted said. I haven't turned it off yet, but everything is still running and my files still seem to be there. Is there any way to save my system? I can back up some of the most important files, but I really don't want to lose all of my customization/ have to re-install anything. Will everything be gone when I restart my computer? A prompt response would be appreciated, I can't keep this thing running forever, I'm not paying the electric bill.

Thanks so much in advance!

---

### Post by scorchgeek on 2008-10-26
If all your files are still there, I have no idea how your hard drive could have actually had the Linux partition deleted. Do the files still open normally? I would just back up everything I could and risk a reboot, but you may want to wait and see if anyone else has more insight on the problem. Have you tried reopening GParted to see if the status has changed?

---

### Post by Gerafin on 2008-10-26
Several hours later, GParted still tells me the entire hard drive is unallocated. If there's no way to fix this, can somebody tell me which folders I should copy & merge in order to keep my settings & stuff?

---

### Post by dracayr on 2008-10-26
all your settings and user data is in your home directory. if you backup your entire home directory, you should be quite safe (If you do it with nautilus, make sure you press ctrl+H first, to unhide the hidden files)

dracayr

---

### Post by BDNiner on 2008-10-26
Copy everything in you home directory include the hidden directories that begin with a ".". Those hidden directories are the ones that contain a lot the configuration files.

Other files would have to depend on what software you were using on the computer.

---

### Post by scorchgeek on 2008-10-26
Look at this thread and see if anything there helps you:

[http://ubuntuforums.org/showthread.php?t=949137&highlight=hard+drive+unallocated](http://ubuntuforums.org/showthread.php?t=949137&highlight=hard+drive+unallocated)

---

### Post by Gerafin on 2008-10-26
Thanks for the help guys, I figured there wouldn't be much to do besides back up. Not looking forward to it, but oh well.

---

