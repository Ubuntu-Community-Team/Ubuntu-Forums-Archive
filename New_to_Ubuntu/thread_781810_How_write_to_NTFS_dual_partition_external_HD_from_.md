---
title: "How write to NTFS dual partition external HD from Feisty"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by swarup on 2008-05-04
I am running a dual boot XP/Feisty, and have an External HD which was a single NTFS partition. Using gparted, I shrank the NTFS partition and added a second partition of type ext3. Now, when I am booted in Feisty I can mount and read from both partitions, but cannot write to the NTFS partition. And just so you know-- I've added NTFS read/write capability in Feisty, but that didn't make any difference.

---

### Post by bpowell2005 on 2008-05-17
I'm new to linux, so bare with me...
But have you added an entry to your /etc/fstab to support this? I haven't had to do this with USB mounted media. However, as an example, here is an /etc/fstab entry of mine.
I have a dual-boot laptop, XP on one half and linux on the other. In linux, I want my windows NTFS partition mounted no matter what every boot...here is my fstab entry:

/dev/sda1 /mnt/win_c ntfs-3g force 0 0

I added the "force" to make it mount even if windows was not shut down gracefully...my Thunderbird depends on files located on the NTFS partition, so I'm sort of hosed if the NTFS fails to mount because it was not shut down clean.

I hope this helps.

Brendan

---

