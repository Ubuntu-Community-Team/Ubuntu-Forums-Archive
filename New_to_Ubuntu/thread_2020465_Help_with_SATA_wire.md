---
title: "Help with SATA wire"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Aupl8ed on 2012-07-08
Let me try to explain properly here and see if you can help me. My old HP laptop crapped out after I had a new HDD installed. The new HDD was Linux based and had Ubuntu as an op sys (which I loved). So before getting rid of the laptop I removed the drive. Yesterday I bought an Apricorn SATA Wire USB to hook to it so that I can get the 7600 songs that are on that drive OFF of it. I have two systems with which to attempt this. Both are Windows, one Vista and one XP.  Both systems will will "see" the drive both in the Device Manager AND in Disk Management. HOWEVER, neither will see it in My Computer so that I can simply access the file system.  Even though it shows in Disk Management, it will not allow me to assign a drive letter to it or do anything else to the drive. I CAN (on the XP machine) change my boot order and boot to the Ubuntu drive though.  Is my issue simply that Windows doesnt want me to access a Linux based drive from within My Computer? Is there anything I can do/try?

---

### Post by Cheesemill on 2012-07-08
Windows can't natively read Linux filesystems.

If you just want to recover some files you can try installing ext2fsd on one of your Windows installations.

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

---

### Post by mcduck on 2012-07-08
Windows only supports Microsoft's own filesystems, and lacks the ability to read any others (like the ones used on Linux, OS X and Unix operating systems).

There is a third-party driver that allows Windows to read Ext2/3/4 filesystems, although it's been a long tome since I've used it so I don't know how well it works these days. (and it sure wasn't perfect even back when I last time sued it, but might be fine for reading the drive and copying your files elsewhere...)

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

..of course you could also just boot the machine with the Linux drive (or any Linux live-CD/USB), mount the Windows drive and copy the files there that way. Linux has no problems writing to Windows filesystems. ;)

---

