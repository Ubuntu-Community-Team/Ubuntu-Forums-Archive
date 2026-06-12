---
title: "sudden blackout crash"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by SonnyE on 2013-01-18
About an hour ago, my screen suddenly went nearly black (black but still powered on) and no key sequences like ctrl-alt-f1 did anything. The only way out that still somehow worked was pressing and holding the power button, resulting in a shutdown. I don't know why it happened. I had 5 tabs open in Firefox, and two Leafpads open, so it could have been a lot of things. Every power manager option for suspend or hibernate was turned off, so it probably wasn't one of those.

The question is how do I get a log report that would show what was going on in the computer when it happened? I've been looking through things in /var/log and some of that shows startup logs, such as syslog, but where's the log for unusual things happening or errors during a session?

The next startup after the blackout took an extra long time, but the session is still going without errors right now.

---

### Post by elgordodude on 2013-01-18
/var/log/dmesg will show you what happened during startup, might be useful, is often lengthy

until it happens again I would suspect a power surge / brownout first, and maybe a hardware error second

---

### Post by oldsoundguy on 2013-01-18
Check your fans!  It could be an overheating problem.

---

### Post by SonnyE on 2013-01-18
I looked at dmsg and dmsg.0 (which I guess is from the previous startup)

This is the extra stuff in dmsg, and it looks like just cleaning up the hard drive from stuff left on it by the crash:

[    2.689954] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.689964] EXT4-fs (sda6): write access will be enabled during recovery
[    3.938889] ACPI: EC: GPE storm detected, transactions will use polling mode
[   27.766737] EXT4-fs (sda6): orphan cleanup on readonly fs
[   27.766763] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 130853
[   27.766986] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 130971
[   27.767012] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 916649
[   27.767087] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 916645
[   27.767120] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 789515
[   27.767170] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 786452
[   27.767193] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 786507
[   27.767216] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 786526
[   27.767278] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 786522
[   27.799983] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 786524
[   27.800007] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 395781
[   27.800115] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 395794
[   27.800194] EXT4-fs (sda6): 12 orphan inodes deleted
[   27.800198] EXT4-fs (sda6): recovery complete
[   28.766916] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   50.194956] Adding 455676k swap on /dev/sda5.  Priority:-1 extents:1 across:455676k

---

