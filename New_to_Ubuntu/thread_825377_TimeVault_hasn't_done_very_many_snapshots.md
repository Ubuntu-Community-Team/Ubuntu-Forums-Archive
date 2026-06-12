---
title: "TimeVault hasn't done very many snapshots"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-06-10
I just installed TimeVault yesterday and set it up using [thi]("http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10-p2")s guide, yet, in the two days I've had it, it's only done 16 snapshots of files. Shouldn't it do a lot when it first gets installed, so that it can create snapshots of all the files I have set it up to watch? Right now it says it's watching 2285 directories, but only 6 files are scheduled to be backed up. On the guy's guide, he has a picture of his TimeVault watching 1677 directories, and about 2400 files are scheduled to be backed up. Why is this so few on mine?

---

### Post by alexandremrj on 2008-06-16
Hello,

when Timevault gets installed it doesn't do a snapshot of your files, you have to do that yourself with the option "Baseline" in Timevault preferences --> Include Tab.

This will create a first snapshot of the files in the include tab and it will only do snapshots of files that changed:

if you watch /etc/ you will have lots of files and directories but there will be only a snapshot when you install programs or change network settings and so on.

---

