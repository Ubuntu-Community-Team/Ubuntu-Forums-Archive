---
title: "Ubuntu installed from within windows xp"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by thejackaloo.co.uk on 2008-07-03
Hi, I thought it would be a good idea to put the ubuntu 8.04 disk in while in windows and install ubuntu in a folder called ubuntu on the c drive. So basically in c:\ubuntu\disks\ there is a file which is the root partition on which ubuntu is installed.

I made it 15Gb but would like to increase it.

No partition editor will do this obviously because the partition is a file and not a proper partition.

Is there any way to resize it ?

---

### Post by iaculallad on 2008-07-03
Try reading this Wubi Guide on [resizing virtual partitions]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b").

---

### Post by fidamehran on 2008-07-03
I'm not sure if I got this right. But I remember seeing an option in Wubi showing "Dynamically Expanding Partition Size".... blah blah. Does that mean that the partition will continue to grow by itself, as new updates and additions are associated with the initial Ubuntu installation? If so, then is there any need to expand/extend/increase the partition size in any other way?
I am stating this point, because I started Wubi and Ubuntu installation with instructions for a 8 GB Ubuntu installation. But now after running for more than a month, my Ubuntu folder size in Windows shows 8.5 GB. Doesn't that mean it increased since its first installation?

---

### Post by thejackaloo.co.uk on 2008-07-03
Excellent, thats it sorted, trawled through hundreds of posts regarding this matter but every one suggested a partition tool that would only see the full ntfs partition.

Thanks for the help.

---

