---
title: "Manually creating casper -rw file"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by jacoby2 on 2014-05-18
Hello guys. I was wondering if there was a way to create the casper -rw file for persistence manually, i.e. via terminal. I've been using Ubuntu 14.04 Live USB with persistence and it ran fine for the last two weeks. Last night, I was installing a bunch of apps (or at least, I thought I was) and I got a few errors after which the terminal froze. I had no idea what went wrong, so I just forced shut down and fell asleep.

This morning, I tried to boot my netbook and the screen went blank after the grub menu and just stayed like that. I figured I must've accidentally updated the kernel and it messed up the system. So I plugged in another USB with another OS in my netbook, booted, browsed to the drive where the casper -rw file was located and deleted it.

This solved one problem. I could boot into Ubuntu alright, except I just didn't have persistence. So is there a way to manually create the persistence file WHILE I'm running Ubuntu? I don't want to do another fresh install as I only have two drives (one for backup and one for Ubuntu) and my backup drive's running Porteus and it always fails to create bootable USBs due to some module issue.

I would also like to know if there's a way to stop Ubuntu from updating kernel so as not to get in the same situation again in the future. Thanks!

---

### Post by sudodus on 2014-05-19
1. You can start from the beginning with Unetbootin or Startup Disk Creator. This is probably the easiest method.

2. You can make the casper-rw file manually. In the future you can make a copy of the casper-rw file and keep it as backup. You can make the file while running Ubuntu, but it cannot be used before you reboot.

3, You can make a casper-rw partition instead of a file. It is actually easier to manage, and you can have it bigger than 4 GB (the maximum size in the FAT32 file system).

See these links

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by oldfred on 2014-05-19
If you are doing that many updates & changes and flash drive is larger then a full install may be a better choice?

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by C.S.Cameron on 2014-05-19
You can create a ext2, (or 3 or 4), partition and name it casper-rw, (Home-rw also possible).
Persistence size is not limited to 4GB as a casper-rw file is.
I can provide a step by step if you prefer.

---

