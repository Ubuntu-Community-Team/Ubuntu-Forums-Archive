---
title: "Vanished ! (USB harddrive gone after reboot)"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by realunreal on 2008-09-25
After installing Ubuntu I could access my USB harddrive from the desktop,  it's now disapeared after a reboot.

When I view (my places - computer) I can see it but can't access it,  I get the following message.

Unable to mount selected volume, only root can mount !

Whats happened ? ? ?

---

### Post by ashmew2 on 2008-09-26
Which version of ubuntu are you using ?

This might help : [http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux#Detecting_USB_hard_drive](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux#Detecting_USB_hard_drive)

---

### Post by Pro-reason on 2008-09-26
Post the output of these commands:

```

cat /etc/fstab
sudo blkid

```

---

