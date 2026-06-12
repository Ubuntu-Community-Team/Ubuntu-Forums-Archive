---
title: "Too Many Kernels!!!"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Tumpster on 2008-09-09
So I'm just cleaning some things out and I was looking at my grub menu and I have a boat load of kernels. Which ones should I keep and which kernel is best to run all the time?? My grub looks like this:

2.6.24-21-rt
(One with "recovery mode")
2.6.21-21-generic
(One with "recovery mode")
2.6-24-20-rt
(One with "recovery mode")
2.6.24-20-generic
(One with "recovery mode")
2.6.24-19-rt
(One with "recovery mode")
2.6-24-19-generic
(One with "recovery mode")  


And so on and so forth all the way down to -11 so I have about 20 different options in my grub. I run linux solely and just wanna clean things up but make sure I have the best one running. By the way, what is "rt?" THanks!:)

---

### Post by kpkeerthi on 2008-09-09
I suggest you keep the 2.6.24-20-generic and [remove the rest]("http://ubuntuforums.org/showthread.php?t=818177").

---

### Post by Sef on 2008-09-09
> I suggest you keep the 2.6.24-20-generic and [remove the rest]("http://ubuntuforums.org/showthread.php?t=818177").


I would keep the two latest kernels.  (one as a back up.)  As to which one to use?  Use the latest one that works well on your system.

---

### Post by rossjman1 on 2008-09-09
If you would like to keep them, but keep them off the grub menu use startupmanager.```
sudo apt-get install startupmanager
```.

---

