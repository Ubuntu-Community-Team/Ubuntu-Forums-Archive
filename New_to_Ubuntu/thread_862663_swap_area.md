---
title: "swap area"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-17
I have Ubuntu installed on /sda3 and /sda4 is the swap area. If I decide to install another OS (Kubuntu, Xubuntu) on /sda3 do I need to do anything with the swap area? 

Thanks,
Ed

---

### Post by bhadotia on 2008-07-17
The distro you are going to install will automatically detect and format the swap partition- you don't need to do anything.

---

### Post by bodhi.zazen on 2008-07-17
No, you can share the swap.

The only problem is that a new OS will occasionally format the swap, thus changing the UUID. If this happens you will need to update the UUID in fstab (in your old OS).

To list your partitions by uuid :

```
sudo blkid
```To update fstab :

```
gksu gedit /etc/fstab
```

---

### Post by bhadotia on 2008-07-17
> No, you can share the swap.
I think, He says that he will remove ubuntu on sda3.
> To list your partitions by uuid :

     Code:
     sudo blkid 
To update fstab :

     Code:
     gksu gedit /etc/fstab 
Also edit the '/etc/initramfs-tools/conf.d/resume' file if you wish to dual -boot- as dual-boot  might cause boot-splash problems in ubuntu. I had that problem and just got it solved an hour ago:[http://ubuntuforums.org/showthread.php?t=848409](http://ubuntuforums.org/showthread.php?t=848409)

---

