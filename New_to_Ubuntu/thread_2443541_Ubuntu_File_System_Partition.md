---
title: "Ubuntu File System Partition"
date: 2020-05-16
forum: New to Ubuntu
---

### Post by icylake on 2020-05-16
Hi all,

I recently installed Ubuntu 20.04 onto an external hard drive. When I looked in the disk, it showed 2 partitions, File system partition 1 & 2, both partitions are relatively small. So I was wondering, what are these two partitions, what do they do and do I need to expand them? Thanks.

Picture of what I am talking about: [https://imgur.com/a/UeVKkEe](https://imgur.com/a/UeVKkEe)

---

### Post by CelticWarrior on 2020-05-17
It seems normal.

There's likely an ESP (EFI System Partition), a boot partition (because of encryption) and the rest is the encrypted partitions (LUKS). Leave it alone or you'll break it.

---

