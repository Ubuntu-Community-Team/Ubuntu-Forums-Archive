---
title: "Creating a copy of a dual boot system"
date: 2016-10-26
forum: New to Ubuntu
---

### Post by rafisham on 2016-10-26
Hi,

I have installed Ubuntu 12.04 LTS using WUBI, along with Windows (using partitioning).
Significant changes were made on this installation, and now I wish to know if there is a way to make a copy of this Ubuntu installation.
To be clear, I'm looking to copy just the Ubuntu part of the installation (I have no need for Windows at the moment).

What are my options?

---

### Post by yancek on 2016-10-26
There is a section at the Wubi Guide site at the link below which tells you how to do this.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

You do know that Wubi is no longer supported and that an installation using Wubi installs Ubuntu inside a windows partition as a program so if you remove windows, you also remove your Ubuntu.  I've never used Wubi so can't say how well the recommendation above will work.

---

### Post by Impavidus on 2016-10-27
The file root.disk, which you can find on your Windows partition, is an image of your Ubuntu partition. You can copy that if you want a backup. There is also this guide telling how to migrate a wubi system to a real dual boot system: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by hakuna_matata on 2016-10-31
> **yancek said:**
> if you remove windows, you also remove your Ubuntu.
It depends how you remove Windows. If you don't remove the files wubildr + wubildr.mbr and folder ubuntu (with subfolders and containing files) on Windows file system and run it from MBR (or EFI boot menu) instead of Windows boot menu, it works without Windows, too.

If you want to run a Wubi installed Ubuntu from MBR, you can copy wubildr.mbr (/host/wubildr.mbr within a Wubi installed Ubuntu) to MBR of your disk (e.g./dev/sda):
```

sudo dd if=/host/wubildr.mbr of=/dev/sda bs=446 count=1
sudo dd if=/host/wubildr.mbr of=/dev/sda bs=512 count=15 seek=1 skip=1

```
The [dd]("https://en.wikipedia.org/wiki/Dd_(Unix)") commands don't copy some bytes of wubildr.mbr (position 447-512) because they should not overwrite the existing partition table of /dev/sda (but the boot loader!)
  
But a Wubi installation without Windows is a tricky configuration, in most cases a migration as Impavidus wrote is the better solution:  
> **Impavidus said:**
> There is also this guide telling how to migrate a wubi system to a real dual boot system: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

