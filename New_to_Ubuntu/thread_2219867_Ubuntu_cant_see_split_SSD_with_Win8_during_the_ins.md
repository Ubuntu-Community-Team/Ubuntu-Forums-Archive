---
title: "Ubuntu cant see split SSD with Win8 during the installation"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by karolis3 on 2014-04-25
Hi guys,

First i have split my 32gb SSD to 20gb for Win8 and whats left for Ubuntu.
Win8 instalation was fine, but during Ubuntu installation it shows me entire 32gb SSD. No signs of Win8 and split SSD partitions.

Do you have idea how to solve it?

```
[COLOR=#2E8B57][FONT=Monaco]Disk /dev/sdb: 32.0 GB, 32017047552 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Units = sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Disk identifier: 0x5ad6d857[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]   Device Boot      Start         End      Blocks   Id  System[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sdb1   *        2048      718847      358400    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]/dev/sdb2          718848    40962047    20121600    7  HPFS/NTFS/exFAT[/FONT][/COLOR]
```

---

### Post by oldfred on 2014-04-25
Was SSD gpt partitioned before.
Or is Windows hibernated or Windows 8 with fast boot on which is always hibernated?

Does gparted show partitions? Often better to manually partition, then use Something else to choose the partition as / (root) with change button.

---

