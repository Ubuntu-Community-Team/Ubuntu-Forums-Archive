---
title: "Re-install windows 7 without removing Ubuntu"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2013-02-17
Hi all,
i have a dual boot and i want to re-install windows 7 without losing my Ubuntu partition. How can i do? I would like a 
step-by-step help cause i was reading many post about the same problem but since i am not an expert it seems to be very difficult.
thank you

---

### Post by waynefoutz on 2013-02-17
Windows will nuke the boot loader, GRUB, but it should leave your Ubuntu install intact. What will happen is it will boot straight into Windows like it did before you installed Ubuntu. All you need is an Ubuntu CD, boot into the live environment, and use it to reinstall GRUB.

A guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by kc1di on 2013-02-17
Hello SchrodingerCat,

It not difficult here is a page that will give you the info you need.

basically you'll need to reinstall window in the same partition it's already in and then you will have to reinstall grub2 to beable to boot ubuntu also.

[http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot]("http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot")

---

### Post by Mark Phelps on 2013-02-18
Are you SURE that Ubuntu is in its own partition? Asking because lots of folks think this is the case, but since they install side-by-side using Wubi, this is NOT the case.  You need to confirm that Ubuntu is in its own partition, otherwise, when you remove Windows, you will remove Ubuntu as well.

---

