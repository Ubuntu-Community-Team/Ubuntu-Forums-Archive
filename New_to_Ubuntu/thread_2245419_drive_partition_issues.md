---
title: "drive partition issues"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by cody_selby on 2014-09-23
Hello one and all,

Am new to this Ubuntu game and have just installed ubuntu alongside existing windows 7. All is fine and dandy and my battered old Asus A54C has had new life breathed into it. But I have a slight issue and the issue is this:  

Before installing Ubuntu, and following a youtube tutorial's advice, I partitioned the hard drive in Windows creating a 40gb unallocated partition for Ubuntu, with windows sitting in the remaining 260 or so gb. But now the home folder only has 25gb remaining and I have a "278gb volume" with windows in it which ubuntu seems to think is a external drive that can be removed. And if I try to tidy windows away in a folder it then won't boot.

So, my question is, is there anyway to lock windows away in its own little box (partition), so that it works ok when I need it but doesn't soil ubuntu with its presence, whilst having the rest of the drive's space in the home folder or a folder that isn't thought of as a "volume"?

Please spell out your answers as if you get too techy on me it might go over my head.

Many thanks,

Cody

---

### Post by kira-yamato-2008 on 2014-09-23
Well first you installed Ubuntu, and that takes up quite a bit of space on it's own. Next Ubuntu by default makes swap space, mine was 3GB. Finally, it seems the file manager (usually PCManFM) Calculates space differently than the disk tool does. For example on my machine it says I habe a 147GB primary partition with 64GB free, but the file manager (PCManFM) says I have 134.4 GB total with 53.0 GB of Free space. I hope that clears up your confusion.

---

### Post by grahammechanical on 2014-09-23
Did you install Ubuntu using wubi.exe? If you did then it is Ubuntu that is in a folder inside Windows.

"Volume" is one of the terms used in Linux to describe a partition. Another term would be "file system." File Manager will list partitions under the heading of "Devices." 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Regards.

---

