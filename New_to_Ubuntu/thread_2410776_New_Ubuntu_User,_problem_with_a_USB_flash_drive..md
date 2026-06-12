---
title: "New Ubuntu User, problem with a USB flash drive."
date: 2019-01-20
forum: New to Ubuntu
---

### Post by fuorryd on 2019-01-20
Hello folks!

I am a relatively new Ubuntu user, and a slightly inclined computer person. I am having issues with a flash drive that got corrupted on my old Mac laptop. It was FAT formatted so it previously worked across the two laptops. I have attempted to use GParted (and the fsck command to repair the drive) to no avail. When I run the lsblk command the flash drive shows up for about 30 seconds then disappears. I ran the lsusb command and I don't really know how to decipher it. I also ran the journalctl/ dmesg command and can post what shows up after I connect the usb dive.

Help would be greatly appreciated!

Thank you!

Don

---

### Post by Autodave on 2019-01-20
It probably has failed: they do that more often than you would think.  Have yo tried it in another machine?  If it won't work in 2 or more machines, it is probably failed.

---

### Post by fuorryd on 2019-01-20
That's what I was afraid of, it would not read on my old laptop either. I just didn't know if I was doing something wrong while trying to salvage it and the files off of it. Thanks for your response!

---

