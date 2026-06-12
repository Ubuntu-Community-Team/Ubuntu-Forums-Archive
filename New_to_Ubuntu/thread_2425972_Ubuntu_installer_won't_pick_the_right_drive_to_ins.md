---
title: "Ubuntu installer won't pick the right drive to install to"
date: 2019-09-03
forum: New to Ubuntu
---

### Post by itslucan on 2019-09-03
Hey everyone,

I am giving Ubuntu a spin, and I currently have Windows 10 installed. When I try to select "Install alongside Windows Boot Manager", it says it is going to change partitions on "/sdb". I checked with g-parted to see which disk this was, and it's my mass storage mechanical drive. I want Ubuntu installed on my fast SSD. Is this possible? Why does it think "Windows Boot Manager" is on the magnetic disk?

---

### Post by CatKiller on 2019-09-03
Boot into Windows and turn off Fast Boot.

---

### Post by yancek on 2019-09-03
The Ubuntu people have been considerate enough to write detailed instructions on this specific topic.  It's at the web site below which has been online for several year and I would also suggest the problem is most likely fastboot or hibernation.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Impavidus on 2019-09-03
I you have multiple hard drives, it's often better to partition manually. Choose "Something else".

And make sure Windows' FastBoot is off.

---

