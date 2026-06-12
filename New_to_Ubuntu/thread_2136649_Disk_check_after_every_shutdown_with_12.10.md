---
title: "Disk check after every shutdown with 12.10"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by surajkr on 2013-04-18
I recently installed Ubuntu 12.10 on a new Dell Inspiron 14z  and I have noticed that even after every  graceful shutdown,  the disk check kicks in at the power up.   I'm able to skip the disk check and everything seems to be working fine.

Please help in debugging this.

Thanks,
Suraj

---

### Post by arubislander on 2013-04-18
Have you already tried letting the disk check run its course? If you skip it, it will attempt to do so at the next boot in the way you describe.

---

### Post by surajkr on 2013-04-18
I did three consecutive shutdown operations and let the disk check to finish everytime.  The laptop still boots up with Disk Check.

Which logs should I check to figure out the reason for kicking off the Disk check.

Thanks,
Suraj

---

### Post by Frogs Hair on 2013-04-18
Open the Disks application and it will display bad sectors if any.There may be a mounting error of some kind , so wait for someone with experience for checking that. Ubuntu used to be set to auto check every 30 boots. Disabling the check is not recommended and doesn't explain the reason why it happens every boot.

---

### Post by patrick0 on 2013-04-29
I'm getting the same thing after ungrading from 12.04 to 12.10, on a netbook. The problem was not there with 12.04, started immediately with the first boot of 12.10. Sometimes after the disk check it will automatically restart, then boot all the way with no further check, but then if I restart I get the disk check again. I've tried manually setting the count of max reboots without disk check, to 30 (it was initially -1), using tune2fs, made no difference. Using tune2fs -l shows the partition being marked as "not clean" every time.

---

