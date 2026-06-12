---
title: "gparted does not create partition table usb drive"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by mystmaiden on 2012-06-03
I am trying to reformat my usb drive. I had used it during my very brief sojourn with windows 7 and it messed it up somehow. However, when I try to create a new partition table, gparted seems to go through the motions but nothing changes. I let it use msdos but is there something that would be better? The attachment is a screen shot of where I am at with it now.

thanks

mystmaiden

---

### Post by ajgreeny on 2012-06-03
When gparted creates a new partition table it does not make a new partition; it leaves unallocated space, which is what you have now.

You now need to click in the unallocated space and make a new partition of whatever filesystem type you wish, fat32, ntfs, ext4, etc etc.  I don't think anything is wrong; you have simply not yet finished the formatting operation.

The msdos table is probably best for your purpose.

---

