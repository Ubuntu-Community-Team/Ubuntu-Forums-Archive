---
title: "White Edubuntu Screen at boot"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by selwynk on 2011-11-15
Hi All

I get a white [COLOR=Black]Edubuntu screen [/COLOR]when I boot my pc. The message that comes up with this white screen is:

Serious errors where found while checking the disk drive for <partitions>
I = ignore S = Skip M = Manual Recovery

OS = Ubuntu 11.10 upgraded from 10.04LTS
GRUB2 duel boot with WindowsXP

Note:
The errors are only found on the two XP partitions.

A while back I did install edubuntu but this was removed. Currently I am opening up a terminal and doing sudo startx which starts my normal 11.10 Linux.

Suggestions on how to boot normally? Should I remove the XP partitions from mounting at boot and if so how do I do this?

Thanks

---

### Post by duke.tim on 2011-11-15
If the problem is with the XP partitions (NTFS filesystem i'm guessing) Start XP up and run

```
Chkdsk /f /r
```

There is the linux equivlent fsck [fsck.ntfs, fsck.fat32 etc..]
but it is generally recommend to let the MS tools fix MS problems.

---

### Post by selwynk on 2012-01-20
Hi

Sorry for the late reply but still no luck....problem persists.

Any more suggestions? The problem is similar to what is reported here 

[https://answers.launchpad.net/ubuntu/+source/grub2/+question/174375](https://answers.launchpad.net/ubuntu/+source/grub2/+question/174375)

Also need to manually start Ubuntu with startx so maybe the problem is related.

Thanks again

---

