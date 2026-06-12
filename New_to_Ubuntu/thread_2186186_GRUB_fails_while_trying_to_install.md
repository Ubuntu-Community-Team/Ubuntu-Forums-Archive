---
title: "GRUB fails while trying to install"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by guadaatenea on 2013-11-06
Any idea on how to solve this? Should I try another version? This is Ubuntu 12.04.3 64bits on an Asus X201e, being installed from a pendrive. (For those who read my other posts, yep, it's me, I seem to keep hitting different walls every time I seem to have solved anything at all)
(just in case, the error message reads, in Spanish: "GRUB installation has failed" - "Unable to install the package <<...>> in </target/>. Installed system won't be able to launch without GRUB bootloader")
After this, it gets stuck on a "we will send an error report and eventually fix it" screen.
I am trying to install Ubuntu alongside Windows 8, which wasn't harmed by this, and the partitions I chose seem never to have happened.



[IMG]https://dl.dropboxusercontent.com/u/85050466/P1030662.JPG[/IMG]

---

### Post by oldfred on 2013-11-06
Is this an Ultrabook? Those use Intel SRT which has some sort of RAID. The standard desktop does not have RAID drivers, but you do not want grub installed to a RAID drive, but just to the efi partition.

You need to make sure you have turned off secure boot, fast boot or hibernation, and Intel SRT. Then remove the RAID meta-data from drive. If you are primarily a Windows user you will want to turn the Intel SRT back on to have its caching. But some just install Ubuntu to the small SSD to make Ubuntu fast.

Other users posted this:
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

More info in link in my signature.

---

