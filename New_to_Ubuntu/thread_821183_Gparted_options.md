---
title: "Gparted options"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rhomp2002 on 2008-06-06
I am multi-booting Linux distros and have a question about Gparted.  I note that when you select the mount point for a partition you have a selection such as /, /boot, swap, etc.  Is there a difference between when you would pick / and when you would pick /boot?  I was wondering that if I wanted to chainloader a distro would I use /boot on the partition where the distro was installed or would I use / on the partition where the distro was installed.  And if / then when would I ever use /boot?

:confused::confused::confused:

---

### Post by Najand on 2008-06-07
/ (root partition) is always nessecarry and should be always selected.
If you wish to install /boot on a different partition you may select it on a different partition, but if you don't do so it would be just a directory in your / (root) partition. You may share your swap partition(s) between different distributions but You need / (root partition) and /boot partition (or directory) for every distributions you have.

---

