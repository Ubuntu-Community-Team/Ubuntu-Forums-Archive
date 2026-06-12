---
title: "Can I install 12.04 over a working 14.04 installation?"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-09-12
I recently "upgraded" my perfectly working 12.04 machine to a clean install of 14.04.  Big mistake.  12.04 worked my dual-displays without a hitch, and getting this to work with 14.04 is a nightmare and for no apparent gain from the so-called upgrade.  So can I boot from a 12.04 US now and have it overwrite the current 14.04 install?  This is a dual-boot machine with W7 and I'd just as soon not have to install it again, too!

---

### Post by yancek on 2014-09-12
Yes.  Use the Something Else option in the installer.  Verify the partition on which you currently have 14.04.  Select to install 12.04 to the current 14.04 partition and select to format only that partition during the installation.  This will overwrite anything on that partition so if you do have data you want to save, move it to another partition or drive before beginning.  If you have other partitions besides windows like a /home partition or a separate data partition, dont' touch them.  Not knowing your setup, drives/partitions, it is not possible to be any more detailed.

---

### Post by riverguy99 on 2014-09-12
Thank you!  That sounds like the workable plan.

---

