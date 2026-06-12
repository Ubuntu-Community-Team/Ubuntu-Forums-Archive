---
title: "Checking the file system via fsck"
date: 2022-05-29
forum: New to Ubuntu
---

### Post by matadrox on 2022-05-29
Hello all! I noticed that fsck wants to check the file system every time the system is booted. While with the ext4 filesystem this was understandable for me, but using the btrfs format, the fsck check should be skipped, am I right? I using Ubuntu 22.04

---

### Post by TheFu on 2022-05-29
[https://btrfs.readthedocs.io/en/latest/btrfs-check.html](https://btrfs.readthedocs.io/en/latest/btrfs-check.html)
I'd let it run, if it where me. At least then it would reset the count.
OTOH, if every boot it asks, then I'd start looking for underlying reasons for the issue. It is corruption at the file system or physical layer?  A bad cable? Anything in the logs or SMART data?

---

### Post by matadrox on 2022-05-29
Thank you for your response. No with the disk nothing is happening. I asked because I recall that btrfs was not checked by fsck as it is with ext4.

---

