---
title: "Re-partitioning my HDD"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Skorzen on 2008-06-23
Hello guys!

My current OS is Ubuntu only. So, to make it easier to install, I copied all my data to an external hard disk and made a complete format, using the 'default' options.

My current partition scheme is the following:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e811f2a1-594c-4535-9b2b-5d74891538c0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=288161f8-066d-4ded-98a9-4cf4888c8aae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

So, now I want to make a new partition for data only, so when I need to format, I don't lose everything. The thing is that I want it to 'auto-mount' when Ubuntu is up, also. I also want to reduce the swap size, but that I know how to do.

I think all I have to do is use GParted, but what cautions I have to consider? Should I edit manually /etc/fstab file?

Please answer this noobish question.

Thanks in advice.

Cheers!

---

### Post by logos34 on 2008-06-23
> **Skorzen said:**
> So, now I want to make a new partition for data only, so when I need to format, I don't lose everything. The thing is that I want it to 'auto-mount' when Ubuntu is up, also. 

Should I edit manually /etc/fstab file?

Yes, like this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Or you might consider making it instead a [separate /home]("http://www.psychocats.net/ubuntu/separatehome"). (In the case of reinstalling/upgrading over ubuntu root partition, all you have to do is point the installer to the /home, but tell it NOT to format.)
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
(-->'Clean install upgrade')

---

