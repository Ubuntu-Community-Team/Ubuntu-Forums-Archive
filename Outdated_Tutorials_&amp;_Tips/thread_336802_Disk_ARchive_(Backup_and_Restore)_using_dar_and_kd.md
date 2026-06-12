---
title: "Disk ARchive (Backup and Restore) using dar and kdar(dar Frontend)"
date: 2007-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by gg234 on 2007-01-12
Dar is a shell command that makes backup of a directory tree and files. Its features include splitting archives over several files, CDs, ZIPs, or floppies, compression, full or differential backups, strong encryption, proper saving and restoration of hard links and extended attributes, remote backup using pipes and external command (such as ssh), and rearrangement of the “slices” of an existing archive. It can now run commands between slices, encrypt archives, and quickly retrieve individual files from differential and full backups. Dar also has external GUI like kdar for Linux,thanks to the well documented API.

This is very detailed guide for all ubuntu users

[Full Article]("http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html")

---

### Post by Andreas_DK on 2008-02-24
KDar is a very nice tool / GUI for DAR. Thereby it is very easy to restore also single files. However, KDar is not in the UBUNTU-repository any longer. And it is impossible for me to compile it from the sources. Does anybody know how to do. I use Ubuntu 7.10.

Has anybody experience with installing  from debian packages (like here [http://ubuntuforums.org/showthread.php?t=500492)?](http://ubuntuforums.org/showthread.php?t=500492)?)

Best regards
Andreas

---

### Post by wickstopher on 2008-02-26
Here is the easiest way that I have found to get Kdar running in Gutsy.

First, install the kdebase-runtime-data package (assuming you are using the GNOME desktop environment...I'm just assuming that if you are running Kubuntu this will already be installed, but of course I'm not sure.  It won't hurt to double-check, either way), which is in the Gutsy repositories.

from a terminal:

```
sudo apt-get install kdebase-runtime-data
```

or, from Synaptic, search for and install kdebase-runtime-data

Tthen, download and install the following two .deb packages from the online Dapper Drake archive.  Some folks have suggested editing sources.list to point to Dapper repositories, but this seems somewhat risky and is definitely more of a hassle than it's worth.

libdar3c2a:
[http://packages.ubuntu.com/dapper/libs/libdar3c2a]("http://packages.ubuntu.com/dapper/libs/libdar3c2a")

kdar:
[http://packages.ubuntu.com/dapper/kde/kdar]("http://packages.ubuntu.com/dapper/kde/kdar")

---

