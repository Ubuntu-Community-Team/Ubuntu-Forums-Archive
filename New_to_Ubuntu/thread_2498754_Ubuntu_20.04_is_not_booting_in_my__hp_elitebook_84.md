---
title: "Ubuntu 20.04 is not booting in my  hp elitebook 8460p"
date: 2024-06-26
forum: New to Ubuntu
---

### Post by tototgrossot on 2024-06-26
After installing successfully Ubuntu 20.04 is not booting.
I am using an SSD 120 Gb hard drive.
I've tried to fix it with boot-repair but i doesn't work.

This is the log that reports boot-repair:
[https://paste.ubuntu.com/p/22tgz7kySM/](https://paste.ubuntu.com/p/22tgz7kySM/)

---

### Post by tea for one on 2024-06-26
Your boot-repair report shows that you have installed in Legacy mode.

Also, it appears that this HP Elitebook 8460p is not UEFI compatible?
How old is this PC?

Possibly, your laptop may not be capable of running Ubuntu 24.04 (see line 43)
Perhaps, an alternative flavour Xubuntu or Lubuntu?

---

### Post by tototgrossot on 2024-06-26
It's 13 years old
In BIOS there is the "UEFI Boot" option but there is this warning: 

The "UEFI Boot" option on this system is provided for development puposes only and is currently NOT fully supported or warranted by HP
Preboot Authetification and Drive Lock are currently NOT supported under the UEFI Boot Mode
HP strongly recommends disabling preboot authetification and Drive lock before enabling UEFI Boot on this system

I've tried to enable it and install again but it's not working either.

I can try Xubuntu or Lubuntu. Don't they have this restriction, these flavour ones?

---

### Post by Rubi1200 on 2024-06-26
I have an old HP laptop with legacy BIOS.

I was able to successfully install Ubuntu MATE 24.04 and Kubuntu 24.04.

But, I do not have an "experimental" UEFI boot option.

If Ubuntu is the only operating system you want on the laptop, then I suggest trying the other versions mentioned by **tea for one**. 

My personal choice is to suggest Lubuntu as being a good option to try.

If, during installation, it warns about an EFI System Partition, just click to ignore and continue. It should, in theory, still install and boot correctly (at least in my testing it did).

If none of the Ubuntu flavours work on the laptop, then consider something like Bodhi Linux or even an Arch-based distribution like EndeavourOS.

---

### Post by tea for one on 2024-06-26
Some older PCs also fail to boot in Legacy mode where a bios_boot partition is present.
The solution is to install in really old-fashioned mode with _one_ partition.

Boot into a &#8220;Try Ubuntu&#8221; live session in Legacy mode
Open terminal and check boot mode
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted > Devices > Create a msdos partition table on the target disk.
Open the installer
Installation type = Manual Installation (Something Else)
Select free space and click the + sign
Create one Primary partition with Ext4 file system and Mount point = / (system root)
Install Grub bootloader to device not to a partition (e.g sda not sda1)
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP not found, ignore it and continue the installation.
The installer will show that only one partition is to be created and formatted.
Continue the installation
Rarely, you may need to flag the partition as boot or bls_boot

My preference is Xubuntu because I'm more familiar with gparted.
Lubuntu uses a different utility (partitionmanager)

---

### Post by tototgrossot on 2024-06-26
I've tried Kubuntu and it works fine. It can boot
Thank you very much for your support

---

