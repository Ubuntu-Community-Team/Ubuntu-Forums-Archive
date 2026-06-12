---
title: "[SOLVED] GRUB gone after XP install to other partition"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Korijn on 2008-07-12
As the title says, I had Windows XP Pro and Linux Ubuntu 8.04 on two seperate partitions. I then reinstalled Windows XP Pro over the old partition and now GRUB is gone!

How do I get it back, since my Linux partitions appear to still be okay?

---

### Post by dracayr on 2008-07-12
from liveCD, open a terminal and type:

```
sudo grub
```
a grub prompt (grub>) will appear. type

```
root (hd0,*partition number of ubuntu*)
setup (hd0)
```
(assuming hd0 is the disk you want to install grub on)

dracayr

---

### Post by marshall.robert on 2008-07-12
i since gutsy i have had to use a different method. so use which one fits best.

use the file browser to mount the ubuntu partition.
then open a terminal and type
```
cd /media/<mount folder, could be just "disk">
sudo grub
find /boot/grub/stage1
```
use the output from the find command to do
```
root (<output eg hd0,0>)
setup (<output eg hd0>)
```

if you get no errors reboot and you should be good.

---

### Post by Korijn on 2008-07-15
Thanks everyone, I ended up doing this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start)

And then changing menu.lst so Ubuntu was set to hd0(0,1) again instead of hd0(0,2).

After that it all worked again.

---

### Post by Cope57 on 2008-07-15
Also note that [Ubuntuguide]("http://ubuntuguide.org") has a good fix for this.

[How to restore GRUB to a partition or MBR with an Ubuntu Live CD]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD")

---

