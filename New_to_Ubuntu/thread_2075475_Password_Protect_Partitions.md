---
title: "Password Protect Partitions"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-10-23
I wanted to password protect other partitions on my HDD so, I used the following code :

**gksu gedit  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla**

and made these changes in that file :

[B]#[Mounting, checking, etc. of internal drives]
#Identity=unix-group:admin
#Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
#ResultActive=auth_admin_keep[/B]

But i am just once asked for password and then i can keep mounting all the partitions. I can add again after i unmount, close and reopen the file manager.

I wish that the system asks for password, **EVERY TIME** i try to access any partition on my HDD or external drive / partition after i unmount it.

How can we do that ?

---

### Post by 3dmatrix on 2012-10-25
Any suggestion from anyone ?

---

