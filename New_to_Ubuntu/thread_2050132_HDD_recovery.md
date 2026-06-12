---
title: "HDD recovery"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by Hammer3344 on 2012-08-30
I am currently trying to recover a windows HDD and or its data at a minimum. It seems that some of the HDD sectors may have gone bad (indicated during a partial backup in which I was able to recover roughly 85% of the user data). I have been unsuccessful however in mounting the HDD under ubuntu, windows, bart pe, debian, and linux mint. The only distro that was able to mount the drive was slackware (dont care much to use it as Im not to fond of KDE). On Ubuntu, I have tried running 
```
sudo ntfsfix /dev/sdc1
``` which indicated that the file system was fixed. Upon trying to mount the drive utilizing the regular mount option in the drop down window, I was provided a rather lengthy error stating that there was an input/output error. I reran ntfsfix to try and solve the issue to no avail. I have also tried ```
sudo fsck /dev/sdc1
``` and was provided with the following output ```
fsck from util-linux 2.20.1
fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for /dev/sdc1

```the last step that I tried to accomplish was running gparted on the HDD in the hopes that it would be able to run a disk check on the HDD aswell, but it was unable to identify the HDD and thus failed.

last note: I tried using the disk utility on Ubuntu and the output was "File system is NOT clean"

I appreciate any assistance you can offer :)

EDIT:
A key point to note is that when trying to boot from the HDD it states that it is missing the SYSTEM file to boot windows.

---

### Post by Grenage on 2012-08-30
You'll likely want to either clone the drive (ddrescue springs to mind), or copy the data off via slackware - as it mounted there.  If that doesn't work, getdataback is probably the best tool for NTFS data recovery.

If the unrecovered data is not that important, you can obviously ignore the above, but bear in mind that the disc is likely dying, and almost certainly can't be considered reliable.  I've only seen a handful of drives generate errors, and then function normally.

---

### Post by coffeecat on 2012-08-30
> **Hammer3344 said:**
> I was provided a rather lengthy error stating that there was an input/output error.

What was the error?

> **Hammer3344 said:**
> 
last note: I tried using the disk utility on Ubuntu and the output was "File system is NOT clean"

... is significant.

It seems that you have only tried ntfsfix in an attempt to repair the NTFS filesystem. Bear in mind this from man ntfsfix:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

When it says that ntfsfix is not a Linux version of chkdsk, it really means that it is not a substitute for chkdsk. If you want to be sure that the filesystem has been checked properly then you need to attach the drive to a Windows system and run chkdsk.

However, even that *might* be potentially problematic if there are bad sectors, so cloning the drive first would be a very good idea, and perhaps running a rescue tool such as Grenage suggests first as well.

---

### Post by Hammer3344 on 2012-08-30
> **Grenage said:**
> You'll likely want to either clone the drive (ddrescue springs to mind), or copy the data off via slackware - as it mounted there. If that doesn't work, getdataback is probably the best tool for NTFS data recovery.
 
If the unrecovered data is not that important, you can obviously ignore the above, but bear in mind that the disc is likely dying, and almost certainly can't be considered reliable. I've only seen a handful of drives generate errors, and then function normally.
 
I was able to recover roughly 85% of the data from the HDD, if its the best I will be able to recover, then the user will just have to be happy with that. I also appreciate the feedback in terms of other forms of recovery/cloning. Once I can safely determine that I have recovered as much data as possible, the HDD will simply be destroyed for security purposes. 
 
I will now mark this as SOLVED due to the feedback provided.
 
Thanks for your help guys.

---

