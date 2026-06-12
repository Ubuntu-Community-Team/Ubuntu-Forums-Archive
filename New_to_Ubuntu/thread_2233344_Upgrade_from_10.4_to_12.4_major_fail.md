---
title: "Upgrade from 10.4 to 12.4 major fail"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by eternity*7 on 2014-07-08
In trying to solve an existing problem realized that still had 10.4 version. So followed the instructions to upgrade incrementally and first upgrade to 12.4. Now unable to get any further that the first screen which brings up the following message.

"The disk drive for / is not ready yet or not present."
"Continue to wait, or Press S to skip mounting or M for manual recovery"

if I wait (overnight) nothing happens. If I press S then get same message but it is the tmp disk drive that is not ready or can't be found. Selecting Skip then boots me out completely.

pressing M gets as far as:
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-57-generic/kernel/drivers/crypto/padlock-sha.ko) : No such device
This means nothing to me though of course the words fatal and error worry me!

---

### Post by Impavidus on 2014-07-08
Updates gone wrong are hard to troubleshoot and upgrading a broken install rarely fixes it. So assuming you have backups of all your important files, the best way forward is to do a clean install of 14.04 (12.04 if you really wish). If you forgot to make the backups, you'll need a live disk to get access to the file system of your broken install. Was the partition encrypted? If so, that will complicate matters.

---

