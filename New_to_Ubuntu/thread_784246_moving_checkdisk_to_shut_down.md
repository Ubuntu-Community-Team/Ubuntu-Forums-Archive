---
title: "moving checkdisk to shut down"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by gutsy goober on 2008-05-06
This has been bugging me: I start up my computer and then the system starts a long checkdisk process.  Is there any way to move the automatic check to system shut down rather than startup?

---

### Post by Paqman on 2008-05-06
This has been mentioned over at Brainstorm as something people want. I'm not aware of a hack to achieve it at the mo.

Are you getting it every boot? Because that's not right. On Hardy you can skip the check by hitting ESC. By default it checks every 30 times the drive is mounted. You can [change the frequency of the disk check](http://ubuntuforums.org/showthread.php?t=300477) if you like.

---

### Post by Munkster on 2008-05-09
It was mentioned in the thread that Paqman linked to but [Autofsck]("https://wiki.ubuntu.com/AutoFsck") has worked well for me, you can set the number of boots before it checks, but more importantly, you can set it to run fsck at shutdown (unattended) rather than at boot time.

---

