---
title: "media not appearing on desktop"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-20
once again after an upgrade,myusb stick wont appear on the desktop
you cant right click on it in places it just opens up?
any suggestions???help
rick:confused:

---

### Post by Nano Geek on 2008-07-21
Is you USB drive being mounted at all, or is it just not appearing on the desktop?

---

### Post by Potatoj316 on 2008-07-21
try this in the terminal 
```
sudo mkdir /media/usbdisk
sudo mount /dev/hdb1 /media/usbdisk
```

then if there are no errors go to /media/usbdisk and see if its there

---

