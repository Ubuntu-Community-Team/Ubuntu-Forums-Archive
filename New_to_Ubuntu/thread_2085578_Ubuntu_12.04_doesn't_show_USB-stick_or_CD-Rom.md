---
title: "Ubuntu 12.04 doesn't show USB-stick or CD-Rom?"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by kramer65 on 2012-11-18
Hello people,

Since my fathers computer was hacked last week I finally convinced him that he should use Ubuntu on his old desktop computer. So I just downloaded and installed Ubuntu 12.04.1 and although slow, it all works fine. The only problem is that I cannot seem to mount a USB-stick or a CD-ROM which I insert in the tray. It doesn't show up in nautilus and doing 'ls' in /media only shows *floppy*, and *floppy0*.

So I installed [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and fired it up. In there I see the Sandisk Cruzer on */dev/sdc*. So I choose analyze, which results in:
> Disk /dev/sdc - 4004 MB / 3819 MiB - CHS 1017 124 62
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 128 (FAT) != 124 (HD)
Warning: Incorrect number of sectors per track 63 (FAT) != 62 (HD)
 1 P FAT32                    0   0 33  1017  42 12    7821280 [NO NAME]

Bad sector count.
No partition is bootable

Since the CD-Rom also doesn't show up in nautilus, I suppose the problem is related.

Would anybody know how I can solve this problem? [SIZE="1"][Please note that it is extremely important that usb-sticks will automount in the future. If it doesn't, there is no use in trying to explain how to manually mount using the terminal. In that case my father and his wife will simply need to buy a new computer.][/SIZE]

---

