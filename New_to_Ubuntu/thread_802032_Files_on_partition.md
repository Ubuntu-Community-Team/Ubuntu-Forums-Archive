---
title: "Files on partition"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by will_col on 2008-05-21
This is my first thread on here, thought I should say I'm glad I've installed Ubuntu 8.04 and I'm deeply impressed with the effort that has gone into it by everybody in your team!

Your forums have helped me a lot, including how to play DVD's, mp3's etc. However, a problem appears to have cropped up.

I recently found an application called Amarok which has taken to my liking :) What has bugged me though is that every time Ubuntu reboots, the files I've added into Amarok from my partition can't be found, so I have to add them all over again. Same goes with adding shortcuts on the desktop to folders in my Windows installation.

My computer is partitioned as thus:
-Ubuntu (20.58GB ext3)
-A partition for storing photo's and music to share between Windows and Linux (107.48GB fat32)
-Windows XP (20.5GB ntfs)

Thanks in advance to any help coming!

---

### Post by kellemes on 2008-05-21
> **will_col said:**
> I recently found an application called Amarok which has taken to my liking :) What has bugged me though is that every time Ubuntu reboots, the files I've added into Amarok from my partition can't be found, so I have to add them all over again. Same goes with adding shortcuts on the desktop to folders in my Windows installation.


Are the partition with mediafiles and the Windows partition mounted when you boot your system?
You need to be sure these partitions are automatically mounted at boot.
A little info on mounting a Windows partition.. [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

