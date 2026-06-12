---
title: "[SOLVED] How to mount a HFS DVD"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Kosimo on 2008-05-24
Hello guys, I've got a DVD burned with a Mac Os X Leopard, and is a HFS (mode 1)... I'm not able to mount it with sudo mount /media/cdrom 
I tried sudo mount -t hfs but doesn't work either...

Could anyone please tell me how can I browse this HFS DVD?   
It is possible to do it in Hardy?

Thank you guys.

---

### Post by unutbu on 2008-05-24
```
gksudo gedit /etc/modules
```
Add to the bottom
```
hfs
hfsplus
```
Reboot.
Now your kernel will load the hfs and hfsplus modules. Hopefully that's all you need to read HFS DVDs.

---

### Post by Kosimo on 2008-05-24
> **unutbu said:**
> ```
gksudo gedit /etc/modules
```
Add to the bottom
```
hfs
hfsplus
```
Reboot.
Now your kernel will load the hfs and hfsplus modules. Hopefully that's all you need to read HFS DVDs.

Hello!

Thank you for your answer.
I added both lines on modules, then I restarted but I'm still getting the same error: Cannot mount the volume: Invalid mount option when attempting to mount the volume "new dvd"

Then on terminal: 
```
sudo mount /media/cdrom
[sudo] password for cosimo: 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any idea?

Thank you again

---

### Post by Kosimo on 2008-05-24
This is my /modules BTW:


```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

# Added for Nero Linux device access
sg

hfs
hfsplus
```

---

### Post by unutbu on 2008-05-24
Try
```
sudo mount -t hfs /dev/scd0 /media/cdrom
```

If that doesn't work, please post

```
cat /etc/fstab
```

---

### Post by Kosimo on 2008-05-24
> **unutbu said:**
> Try
```
sudo mount -t hfs /dev/scd0 /media/cdrom
```

If that doesn't work, please post

```
cat /etc/fstab
```

Still not working :(  ```
sudo mount -t hfs /dev/scd0 /media/cdrom
[sudo] password for cosimo: 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

And here fstab:

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7502401-5914-4309-8897-0c47f52904f8 /               ext3    errors=remount-ro 0       1
# /dev/sda2
UUID=f2efe7c9-0e24-4ad1-ade1-b3136a30d117 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thank you again! ;)

---

### Post by unutbu on 2008-05-24
Let's check that the hfs modules got loaded properly:

```
lsmod | grep hfs
```

---

### Post by Kosimo on 2008-05-24
here we go:

```
 grep hfs
hfsplus                79748  0 
hfs                    49796  0 

```

---

### Post by unutbu on 2008-05-24
Hm. I'm sorry I'm stumped.

---

### Post by Kosimo on 2008-05-24
> **unutbu said:**
> Hm. I'm sorry I'm stumped.

No worries :)  Thanks for helping anyway! ;)

---

### Post by Kosimo on 2008-05-24
Btw, any one else can may give me a hand with this? 
I just burn this DVD using Toast 9.0 in Mac os X Leopard as a Data DVD.

---

### Post by Kosimo on 2008-05-24
I did it!!!!!!!!!!!!!!!!!!!!!!!!!!! :guitar:

I had to choose hfsplus instead of hfs!!!! ;)  


Thank you so much!!!

---

### Post by unutbu on 2008-05-24
Ah, great! I'm glad you found the solution.

---

### Post by zero777zero on 2008-11-19
gksudo gedit /etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
hfs
hfsplus
```

> **unutbu said:**
> Try
```
sudo mount -t hfs /dev/scd0 /media/cdrom
```

If that doesn't work, please post

```
cat /etc/fstab
```

```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cae1ceb1-86e8-486f-a4ba-c28d737ce9d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c122fba1-f1b7-40f3-91f0-dbc20e114443 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

> **unutbu said:**
> Let's check that the hfs modules got loaded properly:

```
lsmod | grep hfs
```

```
:~$ lsmod | grep hfs
hfsplus                81028  0 
hfs                    51588  0 
```


errors i'm getting:
when i try hfsplus
```
:~$ sudo mount -t hfsplus /dev/scd0 /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

when i try hfs
```

:~$ sudo mount -t hfs /dev/scd0 /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

note the cd-rom is dated 1994, when mac was using hfs, hfsplus wasnt out yet

---

