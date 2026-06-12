---
title: "Second Hard Drive to Ubuntu (permanent mount)"
date: 2008-10-15
forum: Philippine Team
---

### Post by zanda on 2008-10-15
Hi Guys,

Ask ko lang help nyo about, mounting a permanent drive
 eto ang mga steps na ginawa ko


1. sudo mkdir /media/newdisk

2. chmod 777 /media/newdisk

3. gedit /etc/fstab

- nag add ako ng line na 
   /dev/sdb1  /media/newdisk vfat defaults 0 0
    
4. sudo mount -a


ngayon ang prob. ko lang is hindi ako mka create ng folder sa new drive since ang owner daw po is root

so ang next step ko is change ng owner

5. sudo chown -R username:group /media/newdisk


problem is permission to denied

any help would be appreciated. btw fat32 po yung ginamit ko sa new drive para madaling ilipat sa windows kung mag ka problem yung pc-- tnx

---

### Post by Nhatz on 2008-10-15
Zanda heto yung line na linagay ko sa /etc/fstab ko...

```
/dev/sdb1	/media/storage	vfat	iocharset=utf8,umask=000	0	0
```

try nyo po baka gumana sa inyo. no tweaking of permissions chuva ever! hehehe :)

ASTIG! :guitar:

---

### Post by zanda on 2008-10-16
> **Nhatz said:**
> Zanda heto yung line na linagay ko sa /etc/fstab ko...

```
/dev/sdb1	/media/storage	vfat	iocharset=utf8,umask=000	0	0
```

try nyo po baka gumana sa inyo. no tweaking of permissions chuva ever! hehehe :)

ASTIG! :guitar:


Sir, :D, works great--- :popcorn: :guitar:

---

