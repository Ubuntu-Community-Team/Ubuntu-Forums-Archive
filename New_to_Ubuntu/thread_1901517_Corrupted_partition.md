---
title: "Corrupted partition"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by gmskel on 2011-12-28
A partition has been corrupted. It's my /home partition


which blows...


Before I realized it was corrupted, I tried mounting it. It wouldn't mount. It was detected as having ext2 file system.

Right now I am posting this from a livecd. Using Gparted, the file system is detected as "unknown" under the partition tree. And I get a warning message stating the following:
Unable to detect file system! Possible reasons are:
The file system is damaged
The file system is unknown to Gparted
There is no file system available (unformatted)
The device entry /dev/sda6 is missing

I would like to recover the partition completely. When I first installed ubuntu I formatted this partition as ext3, so it's odd to me that it was detected as ext2 in the recovery console/terminal/command prompt, what have you..

I'm a complete newb to using linux.

I get the jist of the error.. I suspect it has something to do with how the partition is being read. I hope I can recover the data.

---

### Post by gmskel on 2011-12-28
:popcorn:
AKIRA BUMP

---

### Post by buscaron on 2011-12-28
I, on the other hand, *want* side by side installations.

How do I run two versions of FF without mucking up my system? For  instance, my understanding is that if I enable both the Mozilla stable  and "daily build" PPAs, the package manager will always overwrite FF  with the latest version?

Is there a way to run both stable and "latest build"?

_________________________

[FONT=Times New Roman][maglie calcio](http://www.magliecalcio.org)[/FONT][FONT=Times New Roman]	[/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman][maglia calcio](http://www.magliecalcio.org/maglia-calcio-club-c-83.html)[/FONT][FONT=Times New Roman]	[/FONT][FONT=Times New Roman][/FONT]

---

### Post by Gone fishing on 2011-12-28
Testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) is probably what you want to recover corrupted partitions.

I'd run it from the partedmagic live cd [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

I completely fscked the partition table with a failed install of Freebsd - every partition (about 5) were overwritten and corrupted I got everything back using Testdisk.

---

