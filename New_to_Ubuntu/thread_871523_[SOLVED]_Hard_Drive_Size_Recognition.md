---
title: "[SOLVED] Hard Drive Size Recognition"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by computermesh on 2008-07-27
Hey everyone. First and foremost I would like to thank any and all who help me out on this new thread. I just finally gave up on windows again and decided to port back over to UBUNTU and give it another go. I installed 8.04 and I have a 300GB Hard Drive, however, when I go into the Disk Usage Analyzer, it shows as 534.4GB. Any clues as to why this is happening or how I might be able to fix it to show the correct size? I also noticed that under / it shows after i scan the drive it shows that there are 2.1GB being used. But in the same area where it tells me file system capacity, it says there are actually 4.5GB being used. Very confused. Once again, thanks for all of your help.

---

### Post by eightmillion on 2008-07-27
What does
> df -h
output?

---

### Post by computermesh on 2008-07-27
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             268G  2.3G  252G   1% /
varrun                1.8G  100K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   44K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   39M  1.7G   3% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      268G  2.3G  252G   1% /home/shaun/.gvfs

---

### Post by eightmillion on 2008-07-27
It looks like df is reporting the correct values. This appears to be a bug in Disk Usage Analyzer.

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/220177]("https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/220177")
You might post a comment on the bug report.
As to the difference between 2.1GB being used and 4.5GB. I suspect that it is including the size of your swap partition.

---

