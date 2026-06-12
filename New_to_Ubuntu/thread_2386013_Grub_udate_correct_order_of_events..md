---
title: "Grub udate correct order of events."
date: 2018-02-27
forum: New to Ubuntu
---

### Post by Lin_Mast on 2018-02-27
Ubuntu 16.04 LTS  4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64

I am using grub to boot to a RAID1 root '/' partition (single OS - Linux-only system, old-style MBR partition).
Physical drives are /dev/sda and /dev/sdb, RAID1 is /dev/md0.

The RAID tutorials all recommended installing the GRUB boot loader on both devices of the RAID1 so that the device will still boot in a degraded state if a disk fails.

Well after a couple of reboots and edits of /etc/grub.d/40_custom, then:
```
sudo update-grub
sudo update-initramfs -u -k all
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
```

I finally got it booting properly to the RAID1 /dev/md0 and it self assembles great.

Then after the next periodic software update when a new kernel update was installed, it broke and gave me a grub error on trying to configure after update.  I edited /etc/grub.d/40_custom again and ran all of the commands again.

So which is the proper order for the commands above? - Which ones (or all of them) are necessary when I have to make an edit in /etc/grub.d/ ?
Does update-initramfs need to be run before or after (or both) update-grub?  (I am not sure which steps are dependent on previous steps.)
Does update-grub do make all of the necessary changes, or do I still have to reinstall on /dev/sda and /dev/sdb afterwards each time?
When is update-initramfs required?

The whole boot strapping process (of which data is stored where) is sort of a mystery to me,

---

