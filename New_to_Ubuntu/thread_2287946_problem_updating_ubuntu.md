---
title: "problem updating ubuntu"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-23
When i run Software updater.

A dialog boxes appear:
" Not enough free disk space
  The upgrade needs a total of 74.8M free space on disk '/boot'
  Please free at least an additional 27.3M of disk space on '/boot'
  Empty your trash and remove temporary packages of former installation
  using sudo-apt get clean"

When i run gparted
/dev/sda1  FAT32    /boot/eft            512MiB     4.36MiB
/dev/sda2  ext2      /boot                 244MiB     186.47MiB
/dev/sda3  lvm2 pv ubuntu-klyin-vg   465GiB     465.01GiB
unallocated unallocated

---

### Post by howefield on 2015-07-23
Try removing old kernels with

```
sudo apt-get autoremove
```

---

