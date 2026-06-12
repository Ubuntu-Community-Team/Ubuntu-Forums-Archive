---
title: "Mount FAT32 Windows Partition?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Houli on 2008-05-25
How do I mount my Windows partition in Xubuntu. It is /dev/sda2. I tried sudo mount /dev/sda2 and I get this output ```
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
```

---

### Post by sayakb on 2008-05-25
If it is /dev/sda2, try:
```
sudo mkdir /media/sda2
sudo mount -t /dev/sda2 /media/sda2
```

---

### Post by sisco311 on 2008-05-25
Try:
```
sudo mount -t vfat -o defaults,umask=007,gid=46 /dev/sda2 /mnt
```To mount it at boot time:
```
sudo mkdir /media/sda2
gksu mousepad /etc/fstab
```and add this line:
> /dev/sda2 /media/sda2 vfat defaults,umask=007,gid=46 0 1

---

