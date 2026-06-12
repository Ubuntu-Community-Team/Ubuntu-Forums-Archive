---
title: "autodetect LUKS (dm-crypt) devices"
date: 2007-06-13
forum: Programming Talk
---

### Post by rupert on 2007-06-13
Hi,
how can I detect which devices are dm-crypt encryptet Volumes?
I can do a single one with "cryptsetup isLuks /dev/sda1", but how to scann all drives?

Also I can list all devices with "ls -gG1  /dev/disk/by-id/".

maybe I can do  a "sed" on this, and than check per line from the ls command.
Well I havent been able to create the right sed command, bit to confusing for me...
BUt maybe there is a cleaner way, gnome detects these devices at startup too

thx for your help

---

