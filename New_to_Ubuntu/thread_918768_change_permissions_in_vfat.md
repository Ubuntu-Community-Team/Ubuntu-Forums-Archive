---
title: "change permissions in vfat"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by ArKano on 2008-09-13
Hi!

I've got a problem which is driving me crazy:

I've got a hard drive (/dev/sdb1) mounted in /hd2. The filesystem is vfat and the drive has folders and files in it.

Only su can access those files, but I'd like other users to be able to read an write on those folders.

any help?

Thanks!

---

### Post by handydan918 on 2008-09-13
> **ArKano said:**
> Hi!

I've got a problem which is driving me crazy:

I've got a hard drive (/dev/sdb1) mounted in /hd2. The filesystem is vfat and the drive has folders and files in it.

Only su can access those files, but I'd like other users to be able to read an write on those folders.

any help?

Thanks!

All you can do is change ownership or permissions on the device or mount point itself. vfat (fat16 fat32) and NTFS do not support permissions.

Not sure what you mean "only su can access". There is no root account on Ubu. Do you mean it is prompting you for a password in order to access it? Or is this a different linux?

---

### Post by ArKano on 2008-09-13
Sorry I'm not currently using Ubuntu, I thought you could help me anyway.

Can you tell me how to change ownership of the device or mountpoint?

---

