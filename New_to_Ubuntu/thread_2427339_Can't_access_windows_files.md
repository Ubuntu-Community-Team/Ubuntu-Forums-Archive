---
title: "Can't access windows files"
date: 2019-09-20
forum: New to Ubuntu
---

### Post by myominkyaw on 2019-09-20
I dual boot Windows 10 and Ubuntu, but I can't see my files in :(D) folder. So, I tried to boot Windows back but it show I need to reinstall Windows. I don't want to reinstall it, just need access to my files. What should I do? I am on 19.04 LTS.

---

### Post by TheFu on 2019-09-20
In Windows, have you disabled "fast boot" or "fast startup"?
In Windows, disable hibernation.
In Windows, might the disks be using advanced partitions?  *Basic partitions* work easiest with Linux. 

After you check all these things and verify the boot thing is off, hibernation is disabled and only basic partitions are used for NTFS storage, then Linux can most easily access the partitions. The first 2 issues cannot be fixed or worked around from Linux.

---

### Post by yancek on 2019-09-21
Did this dual boot ever work or is this a new install?  You refer to "D" folder which in windows generally means a data or non-system partition.  Did you make any changes just prior to this problem coming up and if so, what?

---

### Post by Mark Phelps on 2019-09-21
Windows 10 enables FastStartup by default -- and this is a new form of hibernation that keeps the Windows volumes mounted even when Windows is not running.

That prevents Linux from mounting the volumes to access them -- because they remain mounted for Windows.

---

