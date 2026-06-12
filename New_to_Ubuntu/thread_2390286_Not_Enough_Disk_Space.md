---
title: "Not Enough Disk Space"
date: 2018-04-27
forum: New to Ubuntu
---

### Post by gdawgs47 on 2018-04-27
I'm trying to dual boot Ubuntu 18.04 LTS on a Dell Precision 5520, but every time I try I get the error

"You need at least 8.6 GB disk space to install Ubuntu.
This computer has only 7.7 GB."

My hard drive has plenty of space. It keeps using the flash drive as the place to install. I've tried creating a new boot but it didn't change anything. I had the same problem with 16.04 LTS.

---

### Post by yancek on 2018-04-27
Dual boot with what?  You need to have free/unallocated space outside the partitions in use.  If you have some windows system installed, it is likely taking up the entire disk.  If you boot Ubuntu and select Try Ubuntu and get to a Desktop, open a terminal and type the following command and post the output here.  The command will show your drivs/partitions and their sizes.

```
sudo parted -l
```

---

### Post by gdawgs47 on 2018-04-27
Dual Boot with Windows 10

[https://imgur.com/a/k1zev7O](https://imgur.com/a/k1zev7O)

---

### Post by oldfred on 2018-04-27
You show only the flash drive?

If Windows is drive hibernated or fast start up on, which is just hibernation.
Or did you convert a gpt drive to MBR using Windows which does it incorrectly?
Or is BIOS set drive for RAID, not AHCI as it should be?

Just copy & paste terminal output. If longer use code tags which are easy to add with Forum's advanced editor and the # icon. Code tags also preserve formatting.

---

### Post by gdawgs47 on 2018-04-28
I haven't installed it yet but I think I am now able to

[https://imgur.com/a/xn4eWX5](https://imgur.com/a/xn4eWX5)

I switched fast boot from minimal to auto.
I set the drive to RAID instead of AHCL.
Now it is asking me if I'd like to dual boot with Windows Boot Manager and not giving me error messages about insufficient data.

Thank you for the advice!

---

### Post by yancek on 2018-04-28
How big is that NVMe drive?  Your last image shows 512GB all of which is being used by windows partitions.   If that is the size, you need to shrink what shows as partition 3 to create unallocated space.  That in all likelihood would be your "C:\" partition in windows and you can use Disk Management in windows to do that.  If the drive is bigger, that's another story.

---

