---
title: "Cannot mount Volume"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-11
Hi guys,

can anyone help me with this error? seems like no matter what CD i put in i get the error. screen shot is attachedfile:

---

### Post by appoloin on 2008-05-11
i Tried to do update i and get this error too seems something about my CD Rom

---

### Post by bubba_169 on 2008-05-11
Try typing this in a terminal...

```
sudo mkdir /media/cdrom0
```

then try putting a cd in again? Just a thought...

---

### Post by appoloin on 2008-05-11
CD-Rom is fine now but on update i get this error:
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 88.159.206.7 80]
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/hardy/main/source/Sources.gz)  404 Not Found [IP: 88.159.206.7 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bubba_169 on 2008-05-11
Try updating with the hardy heron cd in the drive see if that changes anything?

---

### Post by appoloin on 2008-05-11
you mean try to update with the Ubuntu CD?

---

### Post by appoloin on 2008-05-11
i tried updating with the ubuntu cd in and i still get the msg below

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bubba_169 on 2008-05-11
Go into "System->Administration->software sources" and at the bottom of this window in a white box should be "CD-ROM with ubuntu...". Uncheck this option and see if that helps?

---

### Post by appoloin on 2008-05-11
ok that error about CD-Rom is now gone. thanx

---

