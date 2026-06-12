---
title: "SUID Definition"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ElSean on 2008-05-05
I've been looking, but could anyone point me to a detailed explanation of SUID in the mount command, the man pages were a bit vague?

---

### Post by Oldsoldier2003 on 2008-05-05
> **ElSean said:**
> I've been looking, but could anyone point me to a detailed explanation of SUID in the mount command, the man pages were a bit vague?
short answer:
the suid is a unique (well most of the time) identifier from your hd partition. the reason its used in fstab now is that usb devices can change their mounting position. if you added some usb devices its possible that the device that was /dev/sdc1 could mount as /dev/sdc2 and that would mess up your fstab.

example ```
sudo mount -u 308305b8-a730-4f4f-b152-24e82ff81ec0
```would give the same result as: ```
sudo mount /dev/sda2 on my system
```

```
ls /dev/disk/by-uuid -alh
```gives you a list of devices and their UUIDs

---

