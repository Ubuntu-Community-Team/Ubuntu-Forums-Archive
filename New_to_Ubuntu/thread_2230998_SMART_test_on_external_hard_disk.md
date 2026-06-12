---
title: "SMART test on external hard disk"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-06-22
My external hard disk appears to have died. Yesterday Ubuntu 14.04 didn't boot. gparted reported that fie system unknown with a big exclamation mark. Reformatted and the same thing. I tried to make some room by making a new partition in the same drive and format to ext4. But after unplugged and re-attached gparted again reported file system unknown.

I tried to run SMART with disk utility but the option is greyed out. There was an old bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/743927](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/743927), but it says fix has been released since 12.10. I am on 13.10.

I know there some command line ways to run SMART but I have forgotten what they are.  Any suggestion?

Thanks.

---

### Post by Vladlenin5000 on 2014-06-22
Many external drives don't support SMART. The drive itself does but the  SATA-USB interface doesn't.

---

