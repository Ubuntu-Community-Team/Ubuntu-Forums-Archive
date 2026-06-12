---
title: "Dropbox permission denied on boot"
date: 2016-12-08
forum: New to Ubuntu
---

### Post by caterhamfan on 2016-12-08
Hey all,

Another newbie problem I can't resolve. Ubuntu 16.04 LTS.
Dropbox keeps requesting relinking on bootup (its linked to a partition NTFS). I read this error could happen because dropbox loads before the partition is mounted.

Following the steps here apparently fixes the problem.

[https://ubuntuforums.org/showthread.php?t=2111361](https://ubuntuforums.org/showthread.php?t=2111361)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

As a newbie to Ubuntu this is difficult. Is there a easier graphical way? Or can someone lay out a step by step process? I would be extremely grateful.

Thank you,

---

### Post by Geoffrey_Arndt on 2016-12-09
Perhaps another approach is worth checking out . . 

>   Unlink the Dropbox on Linux to Dropbox on Windows.
>   Reboot and log in to your Linux partition
>   Goto the Software manager/Package manager you use and install Dropbox on the Linux partition
>   Click on Dropbox icon (in Launcher or via Dash search).   That will trigger the download to install the rest of the program and it's home folder on Linux.   NOTE:   be sure to use the same account as on windows.    You can do that for all your machines, and everything will be synced.

---

