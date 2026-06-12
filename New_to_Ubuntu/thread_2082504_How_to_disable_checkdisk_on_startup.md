---
title: "How to disable checkdisk on startup"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by marcellux on 2012-11-09
Hi,

I installed Kubuntu 12.10 64bit, on Acer Aspire 5920 twice.

1. I knew the HDD was defective, and I was getting on every startup a checkdisk running. Annoying but fair enough.

2. I bought a brand new HDD, Seagate 7200rpm 32MB Cache. I installed the same distro from the very same source, and the HDD do not stop getting checked at every startup.

The source is a USB drive. I downloaded the ISO image and installed to it with the built-in program named "startup disk creator".

So, I know the HDD is fine. I just want to DISABLE the checkdisk at sartup.

Thanks in advance for your help!

ps: the checkdisk gives no HDD error as result

---

### Post by Paqman on 2012-11-09
Right, so you're saying you've got a fresh disk and you did a fresh install, but it's still detecting errors that force a fsck on every boot?

Kind of weird that the actual fsck then completes without error.

You can set the interval between disk checks with:
```
sudo tune2fs -c 50 /dev/insert_disk_here
```

This would set it to check every 50 times that disk is mounted. However, if the filesystem reports an error the it'll still trigger fsck next boot. Give it a try and see if you still get a fsck when you reboot. 

If you do then you still have a fault. It may not be the drive itself that's faulty. Normally I'd start looking at drive cables and possibly the controller on the mobo. Your new disk is USB? Was the old one too, or was that SATA?

---

### Post by marcellux on 2012-11-09
Both HDD's are SATA. The USB Drive was just used for installation  because I did not have a DVD to burn the image to. I have to be very  unlucky if both HDD's were bad! There must be something else, like you said, maybe a cable is the problem. Cheers

---

### Post by oldos2er on 2012-11-09
You might want to install the package gnome-disk-utility and check S.M.A.R.T. attributes on the drive. It's not unknown for new hard disks to be defective.

---

### Post by NikTh on 2012-11-09
> **oldos2er said:**
> You might want to install the package gnome-disk-utility and check S.M.A.R.T. attributes on the drive. It's not unknown for new hard disks to be defective.

+1 . 

Alternatively you can install gsmartcontrol . 

Also read [here, from Kubuntu Forums](http://www.kubuntuforums.net/showthread.php?60667-after-clean-install-repeated-errors-force-root-filesystem-to-become-readonly)

Thanks

---

### Post by HiImTye on 2012-11-10
if you have both attached and set to mount in fstab, then it could be running fsck on your second (faulty) disk, you can disable the check on the second disk by changing its' priority to 0
for instance, change
```
 UUID=<UUID> /some/mount/point/ ext4 errors=remount-ro 0 1
```to
```
 UUID=<UUID> /some/mount/point/ ext4 errors=remount-ro 0 0
```

---

### Post by marcellux on 2012-11-12
It was my bad! The HDD is fine, it was a human error caused by me!

I was trying to do the whole thing again with another laptop, when I realized I had chosen ext2 instead of ext4 for the file system....

I re-installed the OS using ext4 and now there is no more any checkdisk running at every system startup!

Thanks anyway for the good will and the time!

---

