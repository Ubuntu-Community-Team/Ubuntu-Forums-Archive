---
title: "Shared folder fails after update"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2012-11-30
My environment is XP with virtualbox running Ubuntu.  Every time i reboot my virtual box I have to mount the shared directory.  If I do an update and try to mount I get the error message of no such device.  I have to install guest editions from virtualbox after the updates to get the folders to share.

Code I use:
```

sudo mount -t vboxsf -o uid=1000,gid=1000 shared /mnt/windows

```

Ive googled all reasons why but I cannot figure out why it wont stay permanently and I have so many issues.

EDIT:
I do have auto-mount set to YES in VirtualBox

---

### Post by graphicsmanx1 on 2012-12-08
bump

---

