---
title: "File permissions"
date: 2017-03-08
forum: New to Ubuntu
---

### Post by doeonethousand on 2017-03-08
Hello!
I just installed Ubuntu and created a NTFS primary partition for data. But I can't modify it's file permissions. Every time I change something in the Permissions tab it is restored immediately to the implicit values (those that are shown in the image). Does anyone knows why is this happening? If so what can I do to change the file permissions on this drive?
I tried with **sudo ****chown -R je:je "/mnt/My Docs (NTFS)" **but with no efect.

Also why isn't there a file system type detected?

Thanks!

---

### Post by oldfred on 2017-03-08
Windows file systems do not support Linux ownership & permissions. So you cannot change.
You do set defaults when you mount the NTFS partition. It will say root but work.
If external drive the defaults should be ok.

If Internal drive, you can edit fstab.
       [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) 

[URL="https://help.ubuntu.com/community/MountingWindowsPartitions"]
[/URL]

---

### Post by doeonethousand on 2017-03-09
Thanks for the info! It helped me a lot although the problem was with the ext4 partition, that's why I had to change it to NTFS. Anyway editing the fstab and restarting the computer solved the problem.

---

### Post by oldrocker99 on 2017-03-09
Glad your problem is solved. Please mark this thread as [SOLVED] using the Thread Tools at the top of the thread.

---

