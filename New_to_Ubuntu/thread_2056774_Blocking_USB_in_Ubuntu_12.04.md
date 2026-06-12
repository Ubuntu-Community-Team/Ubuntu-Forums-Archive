---
title: "Blocking USB in Ubuntu 12.04"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by sreeraju on 2012-09-12
Can any one help me in this issue .
                         I want to block Usb(storage devices only) in Ubuntu 12.04

---

### Post by prshah on 2012-09-12
> **sreeraju said:**
> Can any one help me in this issue .
                         I want to block Usb(storage devices only) in Ubuntu 12.04

Untested: Attempt at your own risk

You can probably blacklist the usb-storage module to prevent it from loading.

Eg:```
echo blacklist usb_storage|sudo tee -a /etc/modprobe.d/blacklist.conf 
```

May need a reboot to take effect, and may also block other storage devices such as USB optical drives/HDDs/etc.

---

### Post by siddharth007 on 2012-09-12
> Open terminal and login as user with sudo privileges

> Issue the following command

```
 mv /lib/modules/3.2.0-29-generic/kernel/drivers/usb/storage/usb-storage.ko /root
```

(remember to give a space between the two paths /lib/modules/3.2.0-29-generic/kernel/drivers/usb/storage/usb-storage.ko  and /root)

Issuing this command causes the usb storage device file usb-storage.ko to move to the location /root
thus diasabling usb mass storage(pendrives,external hard disks or any other storage device)

> Reboot the system and check by inserting a pen-drive to any of the usb ports.

---

