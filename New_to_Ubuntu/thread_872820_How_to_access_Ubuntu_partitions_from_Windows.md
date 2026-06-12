---
title: "How to access Ubuntu partitions from Windows?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by FuzzieLogic on 2008-07-28
Hi all,

So I've installed Ext2IFS from [www.fs-driver.org/](www.fs-driver.org/). I have a separate partition for my files, called /data, which I can access perfectly from Windows XP. 

However, I can't access the Ubuntu root partition or /home - Windows just doesn't "see" them. I'd like to do an install on another computer where /home is on its own partition and can be accessed by both Windows and Ubuntu. Is this possible?

Thanks in advance. :)

---

### Post by halitech on 2008-07-28
should just be a matter of sharing the /home folder the same way you did with /data. I would recommend against sharing / partition, could accidently mess something up when you are accessing it from windows

---

### Post by FuzzieLogic on 2008-07-28
> **halitech said:**
> should just be a matter of sharing the /home folder the same way you did with /data. I would recommend against sharing / partition, could accidently mess something up when you are accessing it from windows
Hi halitech, thanks for the quick reply. I can see why sharing the root would be a bad idea. And yeah, partition sharing - should have just poked around a bit more. Hehe, I feel silly for posting such a simple question now. Thanks again.

---

### Post by halitech on 2008-07-28
I'm no expert so I would recommend following the instructions in this thread

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by coffeecat on 2008-07-28
> **FuzzieLogic said:**
> But uh..how exactly do you share a partition? I don't remember doing anything in particular with /data to make it show up. It was just there from the beginning.

If it's an NTFS or FAT32 partition and is just 'showing up' the installer must have put an entry in /etc/fstab (fstab = file-system table) for you. Which is nice, because it means you are already sharing the partition.

Personally, I would recommend against letting Windows read your root partition (including /home). Some people have reported problems with the ext2ifs driver. What you can do is set up all your folders for personal data in your shared data partition and then set up shortcuts from your Windows 'My Documents' and symlinks (Linux equivalent of shortcuts) from your Linux /home. Then you are accessing and modifying the same data whichever OS you are using.

Post back if you need help in setting up symlinks.

---

### Post by louieb on 2008-07-28
Have you gone into the control panel and use **FS Drives** to make your ext3 partitions visible?

The partitions that each OS can see is dependent on the file system use by that partition.   Ubuntu comes setup to read NTFS and fat partitions  

To see the type of file system used by a partition you can use GParted or the comand **sudo fdisk -l **in Linux.

---

### Post by FuzzieLogic on 2008-07-28
> **louieb said:**
> Have you gone into the control panel and use **FS Drives** to make your ext3 partitions visible?

The partitions that each OS can see is dependent on the file system use by that partition.   Ubuntu comes setup to read NTFS and fat partitions  

To see the type of file system used by a partition you can use GParted or the comand **sudo fdisk -l **in Linux.
louieb - perfect! Exactly what I was looking for. Thank you thank you thank you. :)

---

### Post by FuzzieLogic on 2008-07-28
> **coffeecat said:**
> If it's an NTFS or FAT32 partition and is just 'showing up' the installer must have put an entry in /etc/fstab (fstab = file-system table) for you. Which is nice, because it means you are already sharing the partition.

Personally, I would recommend against letting Windows read your root partition (including /home). Some people have reported problems with the ext2ifs driver. What you can do is set up all your folders for personal data in your shared data partition and then set up shortcuts from your Windows 'My Documents' and symlinks (Linux equivalent of shortcuts) from your Linux /home. Then you are accessing and modifying the same data whichever OS you are using.

Post back if you need help in setting up symlinks.
Hi coffeecat - thanks for the warning. You're right, I think I'll just stick with what I have for now and look into the symlinks. Thanks for the info.

---

