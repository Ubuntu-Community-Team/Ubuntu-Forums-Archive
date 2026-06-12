---
title: "Mounting multiple NTFS hard drives."
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Mythblstr on 2012-12-22
I have a Dell XPS 630I running Windows 7 on it. I want to install Ubuntu on it but I have a question about mounting hard drives with multiple NTFS  partitions. I have 4 hard drives on it  a 2TB, 1TB, and 2 500GB drives. Each drive has multiple NTFS partitions primarily for media files. The 2TB drive is connected by a JMicron JMB36X PCIE-SATA controller card. I am considering weaning myself off of Windows but the first thing I need to know is will I be able to mount all of my partitions easily or is this going to be a monumental task?

---

### Post by irv on 2012-12-22
On every install where I dual booted with Windows, Ubuntu just found all my NTFS partitions and mounted them at startup. In fact I had one partition that I keep all my files and I could get at them from either Windows or Ubuntu.

---

### Post by coffeecat on 2012-12-22
@Mythblstr, all your NTFS partitions will appear in the left pane of the file manager. Simply click on the one(s) you want to access and they will be automounted for you read-write.

More here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by deadflowr on 2012-12-22
> **coffeecat said:**
> @Mythblstr, all your NTFS partitions will appear in the left pane of the file manager. Simply click on the one(s) you want to access and they will be automounted for you read-write.

More here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Yes, exactly.
Also, if your havng problems accessing the windows partitions, check to see if the package ntfs-3g is installed.
You should be able to see the partitions without it but you wouldn't be able to write to them.
It should be installed by default, but you never know(better safe than sorry).

---

### Post by ikt on 2012-12-22
problems mounting NTFS drives is so 2006 :p

---

### Post by Mythblstr on 2012-12-22
Thanks for the quick answers everyone, my next question is about media center extenders. I watch downloaded avi and mp4 video files from Windows 7 to my Xbox. Hate my Xbox and I nave no intention on paying Microsoft their extortion fees for XBox lie to stream Netflix through it anymore. Does anyone have any experience using Ubuntu to stream video stored on my NTFS partitions to a media center extender like the WD Live?
Any comments will be appreciated...

---

### Post by audiomick on 2012-12-22
I reckon that is worth starting a new thread with an appropriate title. People tend to look at the threads in which they think they might have an idea that might help. This thread will attract people who know about partitioning, who don't neccessarily know anything at all about streaming. ;)

---

