---
title: "LUBUNTU How to have NTFS write access ?"
date: 2020-07-29
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-29
Using Lubuntu default file manager.
Trying to write files in NTFS partition not is possible displaying message NTFS READ ONLY.
How to have full NTFS access ? The NTFS partition not has any security acl properties in files and folders.
Thanks for reply.

---

### Post by CelticWarrior on 2020-07-29
The partition is likely hibernated or corrupt.
If this is a dual-boot -or- the partition has been in some way accessed by any Windows 8 or newer then it's likely the first hypotheses. Just boot Windows and disable Fast Startup.
It can also be due to errors so the partition is mounted read-only to prevent further damage. In this case also boot Windows and use the Windows native error correction tools.

You can't fix a NTFS partition in Linux.

---

### Post by aug7744 on 2020-07-30
I has figured how to use NTFS access installing Lubuntu in BTRFS. Thanks for your reply.

---

