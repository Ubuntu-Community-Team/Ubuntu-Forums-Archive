---
title: "Mounted Drive not accessible until touched"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by jaminben on 2014-02-22
Hi,

I've just installed Ubuntu 13.10 and have multiple HDD's attached (internal) and they appear to be mounting automatically when the system boots but nothing can write to them until I manually open them.... once opened they work fine.

How can I allow other programs to use these drives without me having to open them first (touch)?

Thanks

Ben

---

### Post by ajgreeny on 2014-02-22
They are probably not mounting at boot time, but they will still appear in the Places menu even if unmounted.

To get them to mount at boot you will need to edit, as administrator, the /etc/fstab file, but those edits will depend on the formatting of the extra drives present in the machine.

Can you show us the output of ```
sudo fdisk -l
sudo blkid -c /dev/null
```and we can give you more info and details.

---

