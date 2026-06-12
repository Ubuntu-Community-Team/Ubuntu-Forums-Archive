---
title: "XFS Tip: SEPARATE BOOT PARTITION!"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2005-04-08
Ok, I have a fs corruption bug that reproduces quite consistently. Here's how it goes:

1. Uncleanly unmount an XFS partition that contains GRUB. The Reset button is great for this purpose.
2. At next bootup, have GRUB write a change. This could be setup (hd0), or even "savedefault"
3. One of these happens:
   a. An FSCK will turn up hundreds of errors, and files will be deleted.
   b. Your superblock will be gone, GRUB refuses to recognize the drive; then, part (a)
   c. You get lucky and escape unharmed.


This doesn't seem to happen at all with an ext3 /boot partition, and an XFS / partition. Lesson? Put "/boot" on a separate partition!

---

### Post by nad on 2005-04-08
Your system will not boot from a XFS filesystem. If you wish to use XFS, you are correct to make /boot in a separate partition, but with an ext2/3 filesystem. At the point in time that GRUB is loading there is no support for XFS.

BTW, I have found XFS superb and fast at handling large directories of large files (thousands of mp3s).

Dan M

---

