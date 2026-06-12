---
title: "problem running c program"
date: 2011-01-06
forum: Programming Talk
---

### Post by nkv1 on 2011-01-06
I burned Ubuntu 10.10 iso to cd and used try from cd option on system start
i want to run a c program i made at home to test cpu for a project.
package build-essential is installed
compiling code works,
execution does not work.
u have a screenshot of terminal below
[[IMG]http://www.freepichosting.com/image/329690-Screenshot.png[/IMG]]("http://www.freepichosting.com/share/329690-Screenshot.png")

---

### Post by MadCow108 on 2011-01-06
probably the disk is mounted with "noexec" which does not allow executing programs.

type *mount* and look for noexec

sudo mount -o remount,exec /media...
should remount it with executable permissions

---

### Post by Vox754 on 2011-01-06
> **MadCow108 said:**
> probably the disk is mounted with "noexec" which does not allow executing programs.

type *mount* and look for noexec

sudo mount -o remount,exec /media...
should remount it with executable permissions

Apparently, since Ubuntu 10.10 NTFS partitions are auto-mounted without execute permissions.

This is a similar thread: [help "command not found"](http://ubuntuforums.org/showthread.php?t=1636929)

The solution is to remount the partition with execute permissions.

---

### Post by nkv1 on 2011-01-09
Great it works thx all

---

