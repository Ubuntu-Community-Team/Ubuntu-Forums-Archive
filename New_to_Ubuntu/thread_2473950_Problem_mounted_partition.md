---
title: "Problem mounted partition"
date: 2022-04-19
forum: New to Ubuntu
---

### Post by jotauve on 2022-04-19
Hi! 
We ve mounted a usb disk and a network drive in my server (in fstab) where we do some files backups. Them are mounted in /media. We found that.. sometimes if the network drive fails or the usb disk is umounted... then our main hard disk is filled up with the backups and is a big problem cause when this arrives at 100% then nothing works. There is some flag or way to avoid this? thanks!

Jordi

---

### Post by DuckHook on 2022-04-19
*Thread moved to **New to Ubuntu** as the more appropriate forum.*

---

### Post by jotauve on 2022-04-20
> **DuckHook said:**
> *Thread moved to **New to Ubuntu** as the more appropriate forum.*

Thanks, keep waiting some answer, :P

---

### Post by Impavidus on 2022-04-20
Make sure that whatever tool or script you use to create the backups first checks to see if the backup drive is mounted. There are ways to do this using the findmnt command, but you can also simply create an empty file in the directory used as the mountpoint. Call the file not-mounted or something like that. If the file is visible, the filesystem is not mounted and the backup tool will give an error message.

---

### Post by ActionParsnip on 2022-04-20
As stated, run a check first then fire an alert in some fashion, or an email to say it broked.

---

### Post by jotauve on 2022-04-20
> **Impavidus said:**
> Make sure that whatever tool or script you use to create the backups first checks to see if the backup drive is mounted. There are ways to do this using the findmnt command, but you can also simply create an empty file in the directory used as the mountpoint. Call the file not-mounted or something like that. If the file is visible, the filesystem is not mounted and the backup tool will give an error message.

good idea, I will try this, thanks!

---

