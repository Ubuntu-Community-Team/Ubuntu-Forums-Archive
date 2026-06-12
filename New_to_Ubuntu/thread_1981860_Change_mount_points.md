---
title: "Change mount points"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by callguzman on 2012-05-17
I partitioned my drives based on the below video and cannot change the mount point to root (/) and home as in the video.  I downloaded ubuntu straight to my computer from the website without using a disk.  I created a partition for the operating system and an extended one for everything else.

[http://www.youtube.com/watch?v=eSMMs4cfMqY](http://www.youtube.com/watch?v=eSMMs4cfMqY)

I have tried several different things and one is set up correctly as the swap drive but the other two say under "mount point"

/media/sda6
/media/sda7

I need for them to read:
/
/home

Please help!

---

### Post by Daveth on 2012-05-17
so, when you installed it you just went for the standard install, and not the custom install option? The latter would have taken you to a place where you could assign /, /home, and swap to the separate partitions you had already made.

You should write down the names of the partitions as gparted notes them- it is just so easy to format the wrong partition or put the wrong mount point in the wrong place.

If you have only just installed it, and have nothing of consequence in /home, or have a very recent copy of /home of a separate back-up drive, the easiest way is just to re-install via the custom option, pointing the mount points to the correct place.
You can code your way out of it, but i cannot now find the code commands to do that.

---

