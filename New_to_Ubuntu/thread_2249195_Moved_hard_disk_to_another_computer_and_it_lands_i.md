---
title: "Moved hard disk to another computer and it lands in grub rescue"
date: 2014-10-20
forum: New to Ubuntu
---

### Post by craig31 on 2014-10-20
Hi

I removed my hard disk containing my Unbuntu 14.04 server installation to a new computer and it will not boot completely.  I end up at the grub rescue prompt with a message about a HDD not found and the UUID quoted.  I can navigate around the file system with ls and followed the instructions on this page: [http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)   but it kept reporting normal and linux.mod not found.

Thanks
Craig

---

### Post by oldfred on 2014-10-20
Boot-Repair said the reinstall of grub into both sda & sdb failed? Error 126 Exec format error, which I do not know.
Was that just reinstalling grub to MBR, or the full uninstall and reinstall of grub which does require Internet to download a new copy of grub?

You do show versions of grub installed to sda & sdb. If system booted from sda before it still should.
But your fstab shows other partition /mnt/data that does not exist. That should not stop booting, but will give errors.

 Or was the correct grub to boot your system on the drive that had the other partitions?
Or is version different?
If you did not do the full uninstall/reinstall of grub I might try that.

You also may want to house clean older kernels.

---

