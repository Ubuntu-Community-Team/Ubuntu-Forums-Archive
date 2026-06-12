---
title: "UEFI Wiped Boot Partition, Encryted Disk, Boot-Repair Not Repairing"
date: 2014-11-14
forum: New to Ubuntu
---

### Post by andrew-eightwoolsocks on 2014-11-14
Hi,

Goofed around with gparted and deleted a fat32 partition that was clearly the boot partition. I can't get boot-repair to work. (Maybe) further compounding is the fact that the former ubuntu install was fully encrypted (luks).

Here's the boot-repair output. Any ideas would be very, very gratefully accepted.

[http://paste.ubuntu.com/9017463/](http://paste.ubuntu.com/9017463/)

Thanks

---

### Post by oldfred on 2014-11-14
With an UEFI boot and LVM which full drive (except boot partition) encryption uses, you have to have both the efi partition and the /boot partition. Also best to turn off secure boot.

The bios_grub partition is only for BIOS/CSM/Legacy boot and only needs to be 1 or 2 MB and unformatted.

You would have had a FAT32 partition with the boot flag to make it the efi partition and a /boot partition that default installs use ext2.

I would see if testdisk sees those two partitions where your sda1 currently is and if you can restore them.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Boot-Repair cannot fix system as it does not create partitions. And the grub install requires both the /boot partition and the efi partition to install correctly for UEFI boot. And you would have to give the passphrase so it can open the / (root) partition to read fstab and know which partitions are which.

---

### Post by andrew-eightwoolsocks on 2014-11-15
Thanks oldfred. I tried out testdisk, but I think because I'd completely wiped the partition and tried recreating a few times, it couldn't be resolved.

I was able to mount the luks drive via Ubuntu LiveCD, and then also use [http://manpages.ubuntu.com/manpages/trusty/man1/ecryptfs-recover-private.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ecryptfs-recover-private.1.html) to unencrypt my home directory. From there, copied to external drive, reinstalled ubuntu, and back and running.

Phew.

---

