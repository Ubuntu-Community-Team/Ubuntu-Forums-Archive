---
title: "Grub Error"
date: 2022-02-18
forum: New to Ubuntu
---

### Post by jimzeb on 2022-02-18
Hello i  am new in ubuntu and tech in advance. I ma having a problem when it comes to booting. I get this Grub error all the time. i have linked the problem to pastebin so i could get some help using boot repair [https://paste.ubuntu.com/p/ZjHVjYBVY8/](https://paste.ubuntu.com/p/ZjHVjYBVY8/)

---

### Post by oldfred on 2022-02-18
It looks like you have installed in both old BIOS and newer UEFI boot modes to gpt partitioned drive.
Since fstab shows mount of ESP - efi system partition last install was UEFI, so only boot in UEFI boot mode.
And always boot live installer in UEFI boot mode.

Other than for small partitions like the ESP, FAT32 is not recommended. It does not support journel so repairs may be more difficult. And FAT32 cannot have any file over 4GB.

You have multiple duplicate entries in UEFI. Best to houseclean duplicates. Years ago some vendor's UEFI crashed with too many entries. That is fixed if you are running latest UEFI and bit older system.

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

