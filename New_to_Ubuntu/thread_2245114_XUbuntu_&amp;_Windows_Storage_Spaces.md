---
title: "XUbuntu &amp; Windows Storage Spaces"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by luke39 on 2014-09-21
Hi All,

Just experimenting with XUbuntu and I would like to dual boot it with my Windows PC. I've got a 3TB (2x 3TB HDD's in a Mirrored Config) Storage Space setup in Windows 8.1 and was wondering if this Storage Pool would be accessible in XUbuntu? I've played around on the Live CD and could not find anything too promising.  lsblk reports the drives as being **sda **& **sda2, **blkid doesn't show the drives. 

Thoughts? Suggestions?

---

### Post by stalkingwolf on 2014-09-21
generally speaking buntu will be able to access all drives and partitions.  windows unless something has changed will only be able to see windows formatted partitions and drives.

the last i looked windows uses a linux based recovery system but cant read linux file systems .  go figure.

---

