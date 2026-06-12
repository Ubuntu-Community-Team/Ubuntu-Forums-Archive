---
title: "Error using Ubuntu 12.10 Wubi Installer for Windows 8"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Sundarraman on 2012-12-18
Hi,

I'm trying to dual boot ubuntu 12.10 alongside windows 8. I tried to use wubi windows installer to install ubuntu. Now when I restart my laptop it reports some problem with "File: \ubuntu\winboot\wubildr.mbr". However i'm still able to login to windows 8 but not ubuntu. Is it because i'm trying to install ubuntu on a MBR partitioned drive or is it because of windows 8 bootloader being completely different than its older versions.

Any help would be highly appreciated.

Thanks
Sundar

---

### Post by bcbc on 2012-12-18
Are you sure you have a MBR partitioned drive? If you got the computer with Windows 8 preinstalled it's likely a GPT disk, in which case Wubi doesn't work.

---

### Post by Sundarraman on 2012-12-18
Okay, I did "list disk" using the diskpart utility and it shows a * under the GPT column for my drive. So I guess my disk is GPT partitioned like you mentioned. Is there any alternative way to install ubuntu along with windows 8?? or is there any new release scheduled for wubi installer which addresses this issue??

---

### Post by bcbc on 2012-12-18
There's a [bug]("https://bugs.launchpad.net/bugs/694242") filed as 'wishlist' that's had very little activity for quite some time. That's all I know.

Your only option is to install normal dual boot, or to use a virtual machine.

---

### Post by Sundarraman on 2012-12-18
Thank you so much for your quick response. Lets hope for the developers to fix this issue soon.

---

### Post by oldfred on 2012-12-18
Actually with gpt partitioned drives there is no more issue of 4 primary partitions. A full install is then easier to partition. Just use Windows MMC to shrink Windows, reboot several times to get Windows to fix itself & install Ubuntu in the free space.

But if Windows 8 was pre-installed you do have UEFI and have to install Ubuntu in UEFI mode. You then have to use the 64 bit version of 12.10.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

