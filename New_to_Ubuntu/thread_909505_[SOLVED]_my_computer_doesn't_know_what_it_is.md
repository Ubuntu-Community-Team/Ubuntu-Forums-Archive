---
title: "[SOLVED] my computer doesn't know what it is"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-03
how come when I look at the disk usage analyzer it says I have 81 gigabutes of space total, and 4 are being used and 77 are free, but when I go to system moniter it tells me I only have 33 gigs total...

how is this and how to I find out how much I really have

Also I have a similar situation when trying to find out how much ram I have...

---

### Post by dioltas on 2008-09-03
Not sure about the Hard Drive space, havn't used that disk analyser thing.

This might explain linux's usage of ram:
[URL="http://softwaretracker.blogspot.com/2007/08/understand-why-linux-uses-up-all-memory.html"]
http://softwaretracker.blogspot.com/2007/08/understand-why-linux-uses-up-all-memory.html[/URL]

---

### Post by y@w on 2008-09-03
```
df -h
```

Gives you the free space on your drive and

```
free -m
```

Will show you free/used memory. Free RAM is a little interesting in Linux. You'll want to look at the -/+ buffers/cache line to know how much RAM is actually being used.

---

### Post by Too Late on 2008-09-03
When you go to System Monitor and open the File Systems tab, there are two different columns - "Free" and "Available". Disk Usage Analyzer counts the numbers that are in the "free" column. In addition, unlike System Monitor, it "re-counts" the gvfs-fuse-daemon thing.

---

### Post by hyperhopper on 2008-09-03
0.0    

english please---wow- too much info--- also, I am running a different comp with wubi, is there a way to actually see the whole system's available disk space?

---

### Post by Shazaam on 2008-09-03
To expand on Too Late's answer, open Disk Usage Analyzer, go to "Edit-Preferences" and uncheck "gvfs-fuse-daemon". This will clear up some of your confusion.

---

### Post by dioltas on 2008-09-03
Ya, just looked into it. Disk usage analyser counts all harddrives including virtual storage, usb storage, cdrom.
Go to Edit -> Preferences, and uncheck gvfs-fuse-deamon and to get an the storage on your hard drive. If you have a cdrom or usb storage plugged in uncheck them aswell.

The number shown should be close to that in system monitor, but won't be the same because I think system monitor gives a value in GiB where as disk usiage analyser gives it in GB.

---

### Post by hyperhopper on 2008-09-03
what exactly is gvs fuse daemon????

---

### Post by Too Late on 2008-09-03
> **Shazaam said:**
> To expand on Too Late's answer, open Disk Usage Analyzer, go to "Edit-Preferences" and uncheck "gvfs-fuse-daemon". This will clear up some of your confusion.
Cool, I hadn't noticed that, because I haven't used that program. But in the same Preferences windows there's an "Available" column, which does not show the same numbers as System Monitor's corresponding column. Instead, it shows the contents of System Monitor's "Free" column. I would consider this as an Ubuntu bug, since Disk Usage Analyzer is installed by default, so there shouldn't be such "conflict".

---

### Post by dioltas on 2008-09-03
> **hyperhopper said:**
> what exactly is gvs fuse daemon????

I'm not sure to be honest, I think it mounts network storage and other stuff as local harddrives so that applications can access the storage.

Here's a thread on it [http://ubuntuforums.org/showthread.php?t=744501]("http://ubuntuforums.org/showthread.php?t=744501")

---

### Post by Too Late on 2008-09-03
> **dioltas said:**
> Ya, just looked into it. Disk usage analyser counts all harddrives including virtual storage, usb storage, cdrom.
Go to Edit -> Preferences, and uncheck gvfs-fuse-deamon and to get an the storage on your hard drive. If you have a cdrom or usb storage plugged in uncheck them aswell.

The number shown should be close to that in system monitor, but won't be the same because I think system monitor gives a value in GiB where as disk usiage analyser gives it in GB.
Both of them seem to use GiB, even though Disk Usage Analyzer doesn't tell it (another bug...).

Every program listed in this thread (df, disk usage analyzer, system monitor) will only count **mounted** filesystems.

---

### Post by hyperhopper on 2008-09-03
well thank you everybody!

---

### Post by dioltas on 2008-09-03
> **Too Late said:**
> Both of them seem to use GiB, even though Disk Usage Analyzer doesn't tell it (another bug...).

Every program listed in this thread (df, disk usage analyzer, system monitor) will only count **mounted** filesystems.

I could be wrong, but on my machine disk analyzer says /dev/sda1 has 49 GB free, system monitor says 45.3 GiB free.

Seeing as monitor reports less and specifies GiB, i assumed that analyzer was reporting GB.

---

### Post by Shazaam on 2008-09-03
> **Too Late said:**
> Cool, I hadn't noticed that, because I haven't used that program. But in the same Preferences windows there's an "Available" column, which does not show the same numbers as System Monitor's corresponding column. Instead, it shows the contents of System Monitor's "Free" column. I would consider this as an Ubuntu bug, since Disk Usage Analyzer is installed by default, so there shouldn't be such "conflict".

And to further complicate matters gparted shows different numbers than System Monitor and Disk Usage Analyzer.

---

### Post by Too Late on 2008-09-04
> **dioltas said:**
> I could be wrong, but on my machine disk analyzer says /dev/sda1 has 49 GB free, system monitor says 45.3 GiB free.

Seeing as monitor reports less and specifies GiB, i assumed that analyzer was reporting GB.
Yes, but both programs still display quantities in GiB.

If you have fewer columns in System Monitor than me, you aren't probably using the latest version (mine is 2.22.3 on Hardy).

---

