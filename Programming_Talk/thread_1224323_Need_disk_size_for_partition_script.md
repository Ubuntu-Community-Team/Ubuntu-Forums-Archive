---
title: "Need disk size for partition script"
date: 2009-07-27
forum: Programming Talk
---

### Post by ee_guy on 2009-07-27
I'm writing a script that uses sfdisk to partition a usb drive, and I am currently hard coding the sizes in the script.  Instead of changing the script when I get a drive of a different size, I'd like to make the script find out the size of the usb drive and make parititions that are some percentage of the total size.

So, is there a quick way to find out the total size of my flash drive?  

Additionally, how can I find out the address of the first sector on the second partition?

Thanks

---

### Post by ee_guy on 2009-07-28
I found an answer on the OESF forum.  Thanks daniel3000.

This works very well for getting the size of the flash drive:

SDSIZE=`fdisk -l /dev/mmcda | grep "Disk /dev/mmcda" | cut -f 3 -d " "`

Then split the result up as needed.

---

