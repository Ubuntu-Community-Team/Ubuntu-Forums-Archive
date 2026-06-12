---
title: "Can Not delete from/copy to USB 2gb NTFS Pen Drive"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by futureal2032 on 2008-05-30
Hey,
i inserted my **Kingston 2GB USB Pen Drive**
it was automatically detected. And file browser was launched.

When i try to delete files though..it says "read only permissions"

In the "Properties" the Permissions dont get highlighted (i.e. Not editable)

my **pen drive gets mounted at /media/disk**
[B]i tried chown 
[/B]
sudo chown -R "user" "mount"

no success

**i tried every possible combination of chmod command**

**no success... I cant delete files on the pen drive**
i have to  tranfer a lot of things by pen drive and this is very irritating..
**my Pen drive is "ntfs" and i am using Ubuntu 7.04**

---

### Post by powerpleb on 2008-05-30
Have you tried: 

ALT+F2
gksudo nautilus

This opens the file manager with root privileges so you should be able to transfer the files.

---

### Post by futureal2032 on 2008-05-30
> **powerpleb said:**
> Have you tried: 

ALT+F2
gksudo nautilus

This opens the file manager with root privileges so you should be able to transfer the files.

Thanx,
but i have tried every possible solution provided in these forums.. does not work.
read my new post .. 
as far as Pen Drives are concerned.. Ubuntu does not exist for me.

---

### Post by marufaberlin on 2008-05-30
if its formatted with ntfs, that can give some problems with write permissions. Do you have any posibility of copying the files with a WinDoze computer and formatting to Fat?

---

### Post by Bubba64 on 2008-05-30
Have you tried right clicking on what you want removed to highlight it then hold down shift then hitting delete on your keyboard this is a complete delete that does not go to a trash it is gone.

---

