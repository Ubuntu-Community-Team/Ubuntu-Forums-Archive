---
title: "Fsck after boot up"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by rlocone2 on 2016-01-25
Hello All,

I've recently installed 15.04 in a Z170M Skylake system.  I was able to get past grub screen and select Ubuntu.  shortly after that screen I get a message fsck clean.  It doesn't proceed after this message.  I ran a util called Boot-repair.  It generated a long log file.

I attempted to clear the dirty bit from the 2nd partition.  That too didn't correct the issue.  

[http://paste.ubuntu.com/14659582/](http://paste.ubuntu.com/14659582/)

Thanks for your time and attention,

---

### Post by sandyd on 2016-01-25
Moved to *New to Ubuntu*

------------------------------------------

I took a look at the boot repair. For some reason, other than the installation USB, there are no linux installations or partitions on your system.

Did you install Ubuntu by booting to the USB drive, or by installing when inside Windows?

Also, if installing Ubuntu by booting to the USB drive, what partitioning option did you choose?

---

### Post by rlocone2 on 2016-01-26
ubuntu is install here /dev/nvme0n1  I used the USB to install.  Also, I partitioned the drive myself.

---

### Post by sandyd on 2016-01-27
> **rlocone2 said:**
> ubuntu is install here /dev/nvme0n1  I used the USB to install.  Also, I partitioned the drive myself.
Sorry, did not see the device at first glance.

For some reason, boot-repair does not include the NVMe drive in the boot summary.

The fix for Ubuntu 15.10 is available at [http://ubuntuforums.org/showthread.php?t=2309056&p=13419832#post13419832](http://ubuntuforums.org/showthread.php?t=2309056&p=13419832#post13419832). No idea if it works or not on 15.04 as I don't have a NVMe drive.

That being said, Ubuntu 15.04 reaches EOL on February 4th, so it may be worth it to try installing Ubuntu 15.10 if the instructions do not work on 15.04.

---

