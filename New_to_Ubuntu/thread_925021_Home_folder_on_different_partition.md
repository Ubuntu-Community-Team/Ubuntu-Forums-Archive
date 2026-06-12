---
title: "Home folder on different partition"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by avanrens on 2008-09-20
I have reinstalled Ubuntu 8.04 but have my previous home folder on a partition on another drive. How can I get the new installation to use my old home folder.

---

### Post by chronographer on 2008-09-20
you can set it up in fstab. Do you know the location of the other partition? then if you do its easy.

I have done this for a long time, my fstab looks like this:

```
# /dev/sda5
UUID=76c891ac-1308-40ab-a449-6aae404e6d10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=737e4a89-b170-4061-9d9a-47c43dc19230 /home           ext3    relatime        0       2
```

So obviously /dev/sda8 is my /home partition, and /dev/sda5 my root (/) partition.

Hope this helps

---

### Post by philinux on 2008-09-20
```
cat /etc/fstab
```

will show you what you need to change

---

### Post by avanrens on 2008-09-20
I know that it is /dev/sda2, but how do I all the other info.

---

### Post by avanrens on 2008-09-20
My fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a7ecf5cf-7bd8-48b1-8b14-dd3cf414f0fa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6850a294-2138-411a-b6be-a5fd7bf54869 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by chronographer on 2008-09-20
the UUID is unnecessary really. what you could add is: 

```
#My home directory to be mounted at startup
/dev/sda2 /home           ext3    relatime        0       2
```

to the bottom of your fstab. If you are already mounting that drive (look for a /dev/sda2 entry) then comment it out by putting a # at the start.

To edit fstab type 'gksu gedit /etc/fstab'  ... be careful though!

---

### Post by avanrens on 2008-09-20
Thank you, but I think the home folder is not complete as it failed to boot.
I booted from the live CD and reset fstab, its back to normal now. I might wait till  I upgrade next month and use a new home partition. Thanks for all the info.

---

### Post by adsf on 2008-11-05
Thanks, I used your suggestions and it fixed my problem.

The only glitch I had a problem with was that I have changed were my user setup to point mounted drive so when I changed the fstab file I was unable to login.  but that was my only stupid fault and now I am up and running

---

