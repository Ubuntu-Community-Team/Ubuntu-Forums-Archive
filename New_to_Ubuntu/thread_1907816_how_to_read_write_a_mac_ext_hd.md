---
title: "how to read write a mac ext hd"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by DarinB on 2012-01-12
This is my situation I have tons of music on my lucid. 
my sister is visiting me and i want to put the music on an external usb hdd but she only has a mac. 
1. can I read write to a mac external usb hdd... and how? 
2. is it better to format the 250Gb hdd (which i don't have yet) to FAT 32

what do you suggest. 

thanks

---

### Post by Lars Noodén on 2012-01-12
I'd stay away from FAT32 if you value the data.  

Linux can read and write HFS+ formatted drives if the journaling is turned off.  If the drive was formatted with journaling enabled, [journaling can be turned off](https://help.ubuntu.com/community/hfsplus) in OS X.  Once it is turned off, it can be read and written to by Ubuntu with no problems.  I do it all the time.

You might need to install the packages hfsplus, hfsprogs, and hfsutils.

---

### Post by Double.J on 2012-01-12
> **Lars Noodén said:**
> I'd stay away from FAT32 if you value the data.  

Linux can read and write HFS+ formatted drives if the journaling is turned off.  If the drive was formatted with journaling enabled, [journaling can be turned off](https://help.ubuntu.com/community/hfsplus) in OS X.  Once it is turned off, it can be read and written to by Ubuntu with no problems.  I do it all the time.

You might need to install the packages hfsplus, hfsprogs, and hfsutils.

+1 it's not advisable to remove journaling from OS X's root disk, but is completely fine for an external storage. As Lars says FAT32 isn't a good Idea for many reasons, but in the immediate instance the file size limit of just under 4GB is the biggest pain nowadays - especially if sharing with OS X; you may want to keep some pretty large .dmg's on there!

If you wanted the most compatible filesystem the one of choice at the moment is NTFS as NTFS support can easily be added to Linux, OS X and BSD, that said you only need it if you've got windows to consider - for linux/OS X, stick to HFS+ unjournalled :)

If you have the drive permanatly attached, consider creating an entry for it in the /etc/fstab file, so that it is auto mounted as read/write at boot. you could also create a new directory such as /Mac-Share to mount at?

---

