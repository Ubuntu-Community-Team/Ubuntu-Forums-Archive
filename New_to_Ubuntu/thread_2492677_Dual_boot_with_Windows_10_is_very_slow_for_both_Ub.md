---
title: "Dual boot with Windows 10 is very slow for both Ubuntu and Windows on UEFI device"
date: 2023-11-19
forum: New to Ubuntu
---

### Post by mshenouda on 2023-11-19
**I have 500GB, 16GB ram, I7 Windows 10 computer, recently I decided to dual boot with Ubuntu 2022. Both are loading from EFI partition. However, after calling any os from the grub, the boot is so slow, Ubuntu(6 mins), Win10(9 mins). I changed the EFI partition to be the first on the hard disk layout. However, it's still too slow. Attached are snapshots for gparted and df -h commands.**

---

### Post by MAFoElffen on 2023-11-20
That is ridiculous.
```

mafoelffen@msi-ubuntu:~$ systemd-analyze
Startup finished in 27.926s (firmware) + 11.165s (loader) + 9.069s (kernel) + 45.785s (userspace) = 1min 33.946s 
graphical.target reached after 45.616s in userspace

```
Have you checked the SMART error logs on your drives to look at the health, and check for any errors.

Have you done chkdsk on the ntfs volumes and fsck on the ext4 volumes? Have you done defrag on your nfts volumes?

Then do this, and post the results within CODE Tags
```

systemd-analyze critical-chain --no-pager

```

---

