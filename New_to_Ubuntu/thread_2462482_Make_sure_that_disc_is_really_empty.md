---
title: "Make sure that disc is really empty"
date: 2021-05-21
forum: New to Ubuntu
---

### Post by sed_faster on 2021-05-21
Hello everyone,

I have a disc with 5TB on my ubuntu server that I thought it was full with data, just not (apparently). I has this disc on another server, turned off for a long time. This is a result of the command fdisk -l:

```

Disk /dev/sde: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

Before I format or create a new partition table on this disc I want to be sure this disc really empty before I do some stupid. What commands can I use to be absolutely sure that this unit is empty?
Thanks

---

### Post by Impavidus on 2021-05-22
If that's all output you get from fdisk -l, there are no partition table, partitions, filesystems and files on that drive. There could still be remnants of such on the drive, which you may be able to recover using file recovery tools. A recovery tool may be able to recover an entire partition or individual files. In the latter case, expect a huge pile of unsorted files, old versions of files and fragments of files. It's hard to get anything useful from that.

If you want to get rid of all data currently on the drive, just overwrite it with zeros.

---

### Post by ActionParsnip on 2021-05-22
I'd use random data rather than zeros. The ultimate boot CD has disk scrubbers on it as well (useful to have)

---

### Post by sed_faster on 2021-05-29
Thanks to your all help. I will assume which this disc is a new disc (maybe I am doing confusing).

---

