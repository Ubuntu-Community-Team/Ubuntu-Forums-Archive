---
title: "inotify and sysfs"
date: 2010-10-08
forum: Programming Talk
---

### Post by Andruk Tatum on 2010-10-08
I am trying to monitor a file in sysfs ( /sys/devices/platform/hp-wmi/tablet to be exact) for changes, but inotify does not seem to work.

The inotify documentation in the kernel source says that there are limitations on inotify watches on sysfs files, and that those limitations decrease as the kernel matures.  So, is it possible to use inotify on sysfs?  I've tried a very small test application and it does not appear to work.

The application I am trying to make is targeted for tablets.  So then my next question is this: what is the most battery-efficient way to monitor a sysfs file for changes?  Can I convert this file to a event?  Can I monitor the file with poll() or select() without wildly using the battery?  How should I monitor this file?

I've asked on the inotify/incron mailing list and was deferred to ask my question on LKML, but the LKML FAQ mentions that it is inappropriate to ask questions that don't have anything to do with *developing* the kernel.  So, where else should I go to find my answers?

Thanks for your help!

---

### Post by phrostbyte on 2010-10-08
Maybe because sysfs are not files in the "persistent data" sense? It's more of an API into the Linux kernel that happens to look kind of like a set of files. :)

If you get more specific with question (why are needing to use inotify on sysfs), maybe someone can up with a solution.

---

