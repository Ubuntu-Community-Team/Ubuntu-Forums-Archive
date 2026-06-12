---
title: "[SOLVED] Missing hard drive space"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Dyonas on 2008-11-23
I've been using an 8.10 release of Ubuntu for a month or so now, gradually getting used to it and the way it works.  I come from a Windows background so I know nothing about Linux overall.  Anyway, on to the problem at hand!

8Gb partition for Linux with 2Gb swap partition.
3.5Gb shows as used in / on Linux using Disk Analyser

The problem with that is it also shows, at the top, 7.9Gb of 8.0Gb used.  I had a full system backup sitting on the partition of 1.5Gb earlier but it was in root and I used ...
sudo nautilus
to get to the area and delete the file since I don't know any other way.  No big deal, I thought, file was gone so the space should be back.  Off to run another backup but I made a mistake and forgot to dismount external drive, cancelled the job and deleted the file it was going to use.  After both of those I thought the files would be in deleted items but they're nowhere to be found.  As a result I'm missing roughly 3Gb of files and being new to Linux I don't know where they went or how to free up the space again.  I can't even run a browser search, I had to login to another OS just to post this.  Can anyone help with this?  I don't mind following commands but make it very n00b orientated as that's what I am!

---

### Post by drs305 on 2008-11-23
Regarding your first observation, Disk Usage Analyzer also includes the .gvfs virtual files in it's report, essentially doubling the apparent file disk usage. You can disable the gvfs reporting in the DUA preferences.

To verify your disk usage, here is a useful command:
```

df -Th

```

Your trash folders may contain a lot of deleted files and be taking up a lot of space. There can be system trash (files deleted by 'root') in places other than your own trash bin. 

I will refer you to the tutorial I wrote about finding and deleting it, as well as other ways to recover disk space:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by Moop on 2008-11-23
Use gksudo nautilus to empty the trash. You can also use ctrl-h to enable viewing of hidden files.

---

### Post by Dyonas on 2008-11-23
Thanks  :)  It makes sense that the files would be in root's trash but I didn't know it was different to the users, found them via drs305 link and number 6 on the list.  4.2Gb space reclaimed in a few seconds after an hour of head scratching, thanks again!

---

