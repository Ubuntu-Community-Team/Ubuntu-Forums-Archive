---
title: "Drivepooling Software, similar to Stablebit."
date: 2017-01-10
forum: New to Ubuntu
---

### Post by elsmandino2 on 2017-01-10
Hi,

I am attempting to make the leap from Windows to Linux and the one thing holding me back is a decent software equivalent of that provided by Stablebit.

At the moment, Stablebit Drivepool pools all my hard drives into a virtual hard drive.  When transferring files to the system, whole files (i.e. it is not raid software) are transferred to each of the physical hard drives, taking into account space available, temperature and I/O activity.

Stablebit scanner also checks the hard drives to let me know if any of them look likely to fail in the near future.

Can anyone suggest anything similar to this for Linux?

It has been suggested that MergerFS and Snapraid would do me just as well - however, as I am very much a Linux beginner, it is difficult for me to make direct comparisons, based upon the few reviews there are.

Any help would be much appreciated.

---

### Post by Tadaen_Sylvermane on 2017-01-10
Don't know if I would call it drive pooling software but the zfs filesystem is the latest greatest thing imo. Worth a look depending on how many drives you have. [https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

For the scanner you can set up your system to automatically run scans and email you the results. Might take a bit of doing but it's possible.

---

### Post by mörgæs on 2017-01-12
During install you are offered to pool all available drive automagically into one logical drive using Logical Volume Manager. It does not give all the functionality you describe but most of it.

---

