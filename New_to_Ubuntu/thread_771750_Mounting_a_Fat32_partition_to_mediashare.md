---
title: "Mounting a Fat32 partition to /media/share"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by eberndl on 2008-04-27
Hi, so I'm still trying to figure all this out, but I want to be able to share my music and open office documents between windows and HH while I complete my switch. So during installation I made a Fat32 partition, but I couldn't mount it at the time. I want to do that now.

I made a file /media/share.  The Fat32 is /dev/sda6.  Here is my attempt at mounting and the error.
```
sudo mount -t vfat /dev/sda6 /media/share
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any suggestions? 
Thanks!

---

### Post by Paqman on 2008-04-27
Do you want to mount it manually every time, or do you want it mounted at boot? If the latter you want to add a new line to /etc/fstab.

---

### Post by spiderbatdad on 2008-04-27
```
sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sda6 /media/share
```

??

---

### Post by eberndl on 2008-04-27
No Paqman, I don't want to mount it manually each time.
Does spiderbatdad's code make a pemenant mount point?

Thanks to both of you for fast replies!!

---

### Post by spiderbatdad on 2008-04-27
nope thats a one time mount...you could add it to fstab if it works, and you want to mount at boot.

---

### Post by eberndl on 2008-04-27
So...that didn't work superbatdad, I got the same error.

>  wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



I'm concerned about the "bad superblock" part...

---

### Post by eberndl on 2008-04-27
Ok, so I double checked with gparted, and the drive wasn't set up as fat32 for some reason.

So to add it to fstab I do ```
sudo nano /etc/fstab
``` and then ```
/dev/sda6 /media/share vfat iocharset=utf8,umask=000 0 0 
```

Right?

---

