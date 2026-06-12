---
title: "samba file server"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Artanis.ro on 2013-03-08
I want to create a samba file server that I can access from 1 windows 7 pc. My question is, is it possible to have 2 hard disks of 2 TB to be seen as 1 share in windows 7? and if this is possible how will the data be split when 1 of the drives (partition) is full?

---

### Post by prodigy_ on 2013-03-08
> **Artanis.ro said:**
> I want to create a samba file server that I can access from 1 windows 7 pc. My question is, is it possible to have 2 hard disks of 2 TB to be seen as 1 share in windows 7? and if this is possible how will the data be split when 1 of the drives (partition) is full?
Never heard of this being done at samba level. There are at least three solid options though:

- RAID0
Pros: Higher read/write speed. Does exactly what you want. Relatively easy to set up, especially as a fakeRAID if you MB supports that. Data are automatically split between all member disks.
Cons: No redundancy. If one disk fails, you may lose all data on all disks, so having an external backup might be absolutely necessary.

- Spanned volume
Pros: Does exactly what you want. Can be set up on existing system. Data are automatically split between all member disks.
Cons: Same as above.
More info:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

- Subfolder (e.g. the first disk is mounted as **/mnt/share** and the second as **/mnt/share/subshare**)
Pros: Very easy to set up.
Cons: You need to split data manually. Possibly won't work with a non-native file systems on the first disk (not sure since I've never tried this approach).

---

