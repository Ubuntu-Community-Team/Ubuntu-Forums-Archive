---
title: "[SOLVED] backup upgrades fill /boot"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by tuskpc on 2008-06-08
Does anyone know of a way to prevent Ubuntu from saving older files in boot, once they have been upgraded?  It keeps filling up my /boot partition each time it updates.

terminal:
```

ls -C
abi-2.6.24-16-generic      config-2.6.24-16-generic  initrd.img-2.6.24-16-generic      lost+found                    System.map-2.6.24-19-generic
abi-2.6.24-17-generic      config-2.6.24-17-generic  initrd.img-2.6.24-17-generic      memtest86+.bin                vmlinuz-2.6.24-16-generic
abi-2.6.24-19-generic      config-2.6.24-19-generic  initrd.img-2.6.24-17-generic.bak  System.map-2.6.24-16-generic  vmlinuz-2.6.24-17-generic
config-2.6.22-14-generic~  grub                      initrd.img-2.6.24-19-generic      System.map-2.6.24-17-generic  vmlinuz-2.6.24-19-generic
tuskpc@tuskpc-laptop:/boot$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             23189076   7197748  14813364  33% /
varrun                  512892       196    512696   1% /var/run
varlock                 512892         0    512892   0% /var/lock
udev                    512892        52    512840   1% /dev
devshm                  512892        12    512880   1% /dev/shm
lrm                     512892     38176    474716   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sda1                46633     45991         0 100% /boot
/dev/sda6             88583232  76552488   7530940  92% /home
tmpfs                   512892     38176    474716   8% /lib/modules/2.6.24-19-generic/volatile


```

---

### Post by avtolle on 2008-06-08
I don't; but can you not delete the .16 kernel related stuff from Synaptic (mark for complete removal, then apply) as a stop-gap? Surely someone here will know the answer to your question, and can respond. Otherwise, is enlarging the /boot partition an option for you?

---

### Post by Oldsoldier2003 on 2008-06-08
> **avtolle said:**
> I don't; but can you not delete the .16 kernel related stuff from Synaptic (mark for complete removal, then apply) as a stop-gap? Surely someone here will know the answer to your question, and can respond. Otherwise, is enlarging the /boot partition an option for you?

remove it using synaptic. search for linux-image the mark the old kernel images for complete removal

---

### Post by tuskpc on 2008-06-12
Had to do [ $ sudo rm...] a few times before I could get Synaptic to work - kept getting a error after the  [$ sudo dpkg --configure -a ].  Now it's working.  Thanks to everyone who replied.

---

