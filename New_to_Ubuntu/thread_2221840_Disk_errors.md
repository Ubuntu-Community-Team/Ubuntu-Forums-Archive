---
title: "Disk errors"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by ericc3141 on 2014-05-04
I just started running Lubuntu off a flash drive, and I'm getting some disk errors.
I always get 1 disk error when I check on menu immediately after selecting my language.
If I boot to the desktop, it would work for a while before freezing or giving me another error.
If I plug the drive back into Windows, it offers to check for errors, but never finds anything.

Is my flash drive probably failing?

I have Lubuntu 14.04, installed on 4 GB USB 2.0 flash drive with the Universal USB Installer, using a 3 GB persistence file.
I downloaded my iso from the Lubuntu site (normal download), and checked md5sum.
It didn't look like there were any errors during the installation.

---

### Post by walterorlin on 2014-05-04
I think a command to find errors on the disk would be ```
sudo badblocks path to usb drive.
``` The flash drive may be /dev/sdb but it may be different if you have two hard drives or memory card reader. 

Not sure if Windows is designed to check for error on ext4 usb drives.

---

### Post by ericc3141 on 2014-05-04
I'm running a live USB. Will Linux check the disk it's booting from?
I believe my installer formatted my drive to FAT32, so Windows should be able to check it.

---

