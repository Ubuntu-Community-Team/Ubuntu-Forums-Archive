---
title: "nvme/uefi ubuntu/budgie 18.04.1 new install no boot"
date: 2019-02-07
forum: New to Ubuntu
---

### Post by twelvekanaw on 2019-02-07
This is a fresh install on a Toshiba 256 GB SSD in a PCIE adapter for NVMe support. The installation media is a USB drive booting in UEFI mode. The computer is an Optiplex 7010 with Bios freshly updated to version A29 and set to UEFI mode with Secure Boot OFF and Legacy Mode ON. Ive tried a couple of ways but, in this instance, I started with a blank SSD using a GPT partition table and let the installer handle the partition setup. It made an EFI partition formatted fat32 using the balance for an EXT4 partition. Installation was straightforward. I rebooted and got nothing. No bootable partition is seen on nvme0n1 and so can't be selected in the UEFI boot order. I tried the boot-repair utility with no success. Before running boot-repair , I generated a report and paste binned it:
 
[http://paste.ubuntu.com/p/hq4gTc2SmN/](http://paste.ubuntu.com/p/hq4gTc2SmN/)

Thanks for your time looking at this. If I could get a suggestion why this won't boot I'd be glad of it. If I left any info out, please ask.
  ```

``` ok

---

### Post by yancek on 2019-02-07
Not sure this will resolve the problem but, since you have an EFI install, turn off Legacy boot in the BIOS.

Use the install media to change boot priority.  You now have the flash drive set first:  Boot0014
Change that to Boot0010 with the command:  sudo efibootmgr -o 0010 (that's a Lower Case Letter O in the command, not a zero).  That point to the Internal drive and since Ubuntu is the only OS, it might boot.  Your boot repair does not show a grub.cfg file which is unusual.  If efibootmgr does not work, you may need to chroot into the system from the install usb.

---

### Post by twelvekanaw on 2019-02-07
Thanks yancek. I thought first thing to set the SSD first in boot order in the system firmware but the SSD is not offered there as a choice. Nor in the one time boot menu when I view that - which, if it was there it would be the other place, too. I'm not sure what to do with chroot. I'll spend some more time reading what I can find about boot fixes. 

To me, it seems like this setup is not far from working. I booted this NVMe drive the first time in a far more complicated scheme that I set up more or less by accident by installing to the SSD in legacy mode. I ended up booting it in legacy mode off a hard drive with W7/Bionic B dual boot on it. In that arrangement, grub does offer the SSD installation as a boot choice (after running boot-repair and finding it with the os probe and writing it in) though the BIOS does not even see it. At boot time, grub complains that there's no such device as the UUID of the SSD and then boots it anyway after a while. It's weird. Ditching Windows and making a UEFI installation seemed like the simple choice compared to that. Strangely, though, I can boot the Frankenstein thing I put together by accident in legacy mode but not the UEFI installation I replaced it with.

I'll try following your suggestions soon. I need to know more about what you mean to do with chroot. No grub.cfg would tend to slow things down I expect. the sudo efibootmgr -o 0010 thing is a new one on me, too. I'll try it all though. Any other thoughts are welcome. I'm kind of feeling my way through this.

---

