---
title: "hibernate not working"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Samrat Rao on 2008-07-11
i changed the swap partition of my ubuntu 7.10. now i am unable to use the hibernate option. the error message is:
'The resume partition is not set up. Probably you need to add a 'resume=...' option to your kernel command line and reboot. Suspend to disk and resume is not possible without a resume partition, please consult the documentation. You can skip this check by setting SUSPEND2DISK_SKIP_RESUME_CHECK to 'yes' in the sleep configuration file.'
what do i do?

---

### Post by soxs on 2008-07-11
as you edited your swap partition it's UUID changed, which is normally used to mount it to your fs.
So get the new UUID:
```
sudo blkid
```

open fstab:
```
sudo nano /etc/fstab
```
replace the UUID of your swap partition with the one you got from blkid and make sure you removed any "
-> ```
sudo reboot
``` or ```
sudo init 6
```

---

### Post by Samrat Rao on 2008-07-11
> **soxs said:**
> as you edited your swap partition it's UUID changed, which is normally used to mount it to your fs.
So get the new UUID:
```
sudo blkid
```

open fstab:
```
sudo nano /etc/fstab
```
replace the UUID of your swap partition with the one you got from blkid and make sure you removed any "
-> ```
sudo reboot
``` or ```
sudo init 6
```

i did change the UUID in /etc/fstab and the swap is mounting properly. i have not tried what you just said i.e. sudo reboot or sudo init 6 as my pc which is having this problem is a kilometer away with no net connection. if you don't mind, will just typing sudo reboot or sudo init 6 help me hibernate the system?
will there be any problems with the installation if i increase root partition size using live dvd? i have allocated space adjacent to the root partition?

---

### Post by louieb on 2008-07-11
**Hibernate Broken**

     To get hibernate to work again had to put correct UUID for swap in 2 places.
     /etc/fstab
/etc/initramfs-tools/conf.d/resume
     After correcting the UUID run:
```
sudo dpkg-reconfigure  initramfs-tools
    
```

---

### Post by Samrat Rao on 2008-07-11
updating /etc/fstab and /etc/initramfs-tools/conf.d/resume unabled the hibernate option to start working, but the pc will not restart, i.e. all i get is the ubuntu logan and the white horizontal bar at the centre of the screen. nothing happens after that.
i have windows xp installed as well. there were some bad sectors (i guess near boot sector). now they are repaired. but while booting ubuntu, the message keeps appearing: 'there are differences between boot sector and its backup'. any way to solve this problem as well?

---

### Post by Samrat Rao on 2008-07-11
> **Samrat Rao said:**
> updating /etc/fstab and /etc/initramfs-tools/conf.d/resume unabled the hibernate option to start working, but the pc will not restart, i.e. all i get is the ubuntu logan and the white horizontal bar at the centre of the screen. nothing happens after that.
i have windows xp installed as well. there were some bad sectors (i guess near boot sector). now they are repaired. but while booting ubuntu, the message keeps appearing: 'there are differences between boot sector and its backup'. any way to solve this problem as well?

i haven't yet received a reply for my above problem. pl help as i need to use the hibernate option.

---

### Post by louieb on 2008-07-11
Just wondering what you did to your swap partition. Did you shrink it? It needs to be larger that the amount of ram.  That and the files you need to check when the uuid for swap changes is  all I know about hibernation. 

As far as the message  'there are differences between boot sector and its backup'. I believe windows keeps a copy somewhere. Are you sure the message isn't coming out of windows? Maybe your anti-virus program:confused:

Not much help but at least you'll get a bump.

---

### Post by Samrat Rao on 2008-07-12
> **louieb said:**
> Just wondering what you did to your swap partition. Did you shrink it? It needs to be larger that the amount of ram.  That and the files you need to check when the uuid for swap changes is  all I know about hibernation. 

As far as the message  'there are differences between boot sector and its backup'. I believe windows keeps a copy somewhere. Are you sure the message isn't coming out of windows? Maybe your anti-virus program:confused:

Not much help but at least you'll get a bump.

the swap size is not likely to be a problem as its size (both before and after changing) is more than the amount of ram and whats more i actually slightly increased the swap size. my friend too has the same installation (ubuntu 7.10) and he has the same hibernation problem although he did not change anything in his installation. his pc specs are different from mine as well.
i do not know whether windows keeps a copy somewhere and neither do i know whether or not the message isn't coming out of windows. how do i find out?

---

### Post by soxs on 2008-07-12
Did you activate swap?
I somewhere read that you need to run a command like swap on or similar (don't remember).
If this is lacking, hibernate won't work.

---

### Post by Samrat Rao on 2008-07-12
> **soxs said:**
> Did you activate swap?
I somewhere read that you need to run a command like swap on or similar (don't remember).
If this is lacking, hibernate won't work.

swap is on without using command like 'swapon' as i can see that the swap partition is mounted when i use 'gparted'. using system monitor also shows that swap is on.

---

### Post by soxs on 2008-07-12
> **Samrat Rao said:**
> swap is on without using command like 'swapon' as i can see that the swap partition is mounted when i use 'gparted'. using system monitor also shows that swap is on.

I were not shure about, if mounting will make the PC actually use the swap, I thought the swapon command would be required additionally?? (I don't know much about swap)

---

