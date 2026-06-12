---
title: "Can't dual boot back into windows"
date: 2018-07-25
forum: New to Ubuntu
---

### Post by circuit8 on 2018-07-25
Hi guys,

I installed windows on my new build. Then installed Ubuntu along side but when I boot up now the grub menu does not appear and it just boots into Ubuntu.

I tried `boot-repair` but it didn't work. Here is the link to the results: [http://paste.ubuntu.com/p/nmhhG9WFRN/](http://paste.ubuntu.com/p/nmhhG9WFRN/)

Thanks in advance!

---

### Post by yancek on 2018-07-25
Your basic problem reported in boot repair is that you left your windows system hibernated when you installed Ubuntu.  If it is hibernated it is mounted and no Linux system will try to mount a hibernated system so you will need to turn it off in the BIOS as well as boot into windows and turn it off.  If you don't have a windows install DVD, you could use the Recovery CD of windows and try the Repair option to see if you can boot it.  If a partition is not mounted, there is no access to the boot files and there will be no menuentry in Grub for it.

---

