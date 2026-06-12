---
title: "Need some help with hard drives"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by ooleyguy on 2013-01-28
I installed Ubuntu 12.04.1 LTS on a 120 GB HD and have several other hard drives that I want to put music, video, and other none executables on. I saw something about symlinks (I think that's what they were called)? Is there a way to partition those other drives and make programs save files there instead of on my system drive?

---

### Post by furything on 2013-01-28
The approach I would use is to add a hard drive and use fstab to mount a location - see here
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

You can just mount the drive and access in /media folder as an extra drive or you could map a hard drive directly to your home music folder say.

---

