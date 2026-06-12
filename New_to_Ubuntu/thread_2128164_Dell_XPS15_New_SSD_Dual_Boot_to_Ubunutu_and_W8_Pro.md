---
title: "Dell XPS15 New SSD Dual Boot to Ubunutu and W8 Problems"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by Juice370 on 2013-03-22
I've been toying with the idea of using Ubuntu for a while, last night I took the plunge... not the best start if I'm honest. I have a new Dell XPS15, I replaced the HD for a 250GB Samsung SSD, it also has the 32GB cache with Intel Rapid Storage Technology. So I disabled the IRST, switch to legacy boot and replaced the HD, then installed W8 to the 250GB drive. Loaded Ubuntu and selected the first option to run alongside W8. In retrospect I think I should have manually set up dual-boot as a better option using EasyBCD.

The problem is that when installing Ubuntu I was never given the opportunity to determine the partitions like it said I would be give in the install notes. Ubuntu has installed on the 32GB cache drive. 

So to fix I then started again and reinstalled W8 to the 250GB HD thinking it would somehow remove Ubuntu form the cache as I want to use that for the IRST as the laptop did from new. Problem now is that when I try to boot from UEFI, it goes looking for Ubuntu and I get the grub error. I can boot without problems to W8 using Legacy.

If anyone knows how to remove Ubuntu from the 32GB cache and reactive the IRST and allow it to boot from UEFI again that would be much appreciated. I'm totally lost. I'll then reinstall Ubuntu using the manual partition method.


Thanks

---

### Post by oldfred on 2013-03-22
The Intel SRT uses RAID. It used to be that Ubuntu would not even install with RAID meta-data on drive, but it seems to install, but then grub sees meta-data and does not install. Standard desktop does not have the extra drivers for RAID that grub needs to install with RAID.

Not sure sure what format Intel needs on SSD and if it will create it automatically. But you should use gparted and remove the Linux partitions.

Are you in BIOS/Legacy mode, not UEFI. It should not be critical which you use, but both Windows & Ubuntu have to be in the same mode.
If in UEFI mode both drives have to be gpt partitioned. If in BIOS mode you have to use MBR as Windows only boots from gpt partitioned drives with UEFI. Ubuntu will boot from gpt drives in either UEFI or BIOS, so how you boot installer is how it installs. So you have to be sure to boot install in correct mode.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Not sure if you converted to BIOS/MBR if this works.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

Others reported this:
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

