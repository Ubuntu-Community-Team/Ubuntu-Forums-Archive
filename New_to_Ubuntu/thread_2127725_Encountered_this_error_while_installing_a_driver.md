---
title: "Encountered this error while installing a driver"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by panaro975 on 2013-03-20
I was installing a legacy driver for my graphics card via the terminal when this error popped up
```
Error! Problems with depmod detected.  Automatically uninstalling this module.DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing fglrx-legacy (--configure):
 subprocess installed post-installation script returned error exit status 6
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic
cp: reading `/lib/modules/3.5.0-26-generic/kernel/fs/reiserfs/reiserfs.ko': Input/output error
cp: failed to extend `/tmp/mkinitramfs_kHq8Pk//lib/modules/3.5.0-26-generic/kernel/fs/reiserfs/reiserfs.ko': Input/output error
WARNING: Couldn't find symtab and strtab in module /tmp/mkinitramfs_kHq8Pk/lib/modules/3.5.0-26-generic/kernel/fs/reiserfs/reiserfs.ko
Errors were encountered while processing:
 fglrx-legacy
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Any help would be greatly appreciated.

---

