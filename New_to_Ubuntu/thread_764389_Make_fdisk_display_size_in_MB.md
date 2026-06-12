---
title: "Make fdisk display size in MB?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by oxsyn on 2008-04-23
If I do "sudo fdisk -l" I see the disk size in blocks.  Is there a way to display it in MB?

---

### Post by Monicker on 2008-04-23
> **F4RR4R said:**
> If I do "sudo fdisk -l" I see the disk size in blocks.  Is there a way to display it in MB?

The total size of the disk, or each partition on the disk?  fdisk -l shows the size of the drive as the top line.

For seeing the size of partitions in megabytes, do "df -h"

---

### Post by SOULRiDER on 2008-04-23
> **Monicker said:**
> 
For seeing the size of partitions in megabytes, do "df -h"

I believe that will only show size of mounted partitions and not all partitions.

---

### Post by niteshifter on 2008-04-23
Hi,

> If I do "sudo fdisk -l" I see the disk size in blocks. Is there a way to display it in MB?

With fdisk, no. Size in blocks is all there is. However these two utilities will:

There's sfdisk:
```
sudo sfdisk -l -uM
```

which generates a report ala fdisk. The -uM specifies report sizes in MB.

There's also cfdisk:
```
sudo cfdisk
```

Press the u key to cycle through the size in sectors, cylinders or M-bytes.
Press Shift+Q to exit cfdisk.


_Of the two sfdisk is the safest one to use for inspection._ I'd avoid cfdisk unless / until one has some experience using ncurses-based console programs.

Both are in the repositories, but usually are already installed.

---

### Post by Gen2ly on 2009-04-11
Never found a way to have fdisk display in MBs but blocks can be easily converted to megabytes with bc:

```
echo "BLOCKS/(2^20)" | bc
```

Gigabytes are 2^30.

---

### Post by forger on 2009-07-08
```
sudo parted -l
``` ;)

---

