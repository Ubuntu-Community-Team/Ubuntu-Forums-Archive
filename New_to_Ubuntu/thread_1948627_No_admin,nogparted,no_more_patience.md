---
title: "No admin,nogparted,no more patience"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by ButchButchButch on 2012-03-28
Hi folks. Right to it,
I forgot my admin password, 
without admin i cant get gparted to destroy partitions for clean install.

Aside from big magnets and cursing, how do I wipe this machine (older sony vaio) so I can start from scratch. 

I have tried to reset password from drop boot in recovery mode.
I get a failure message about a " manipulation token ,and your mom wears army boots,no password change for you." 
Any help would be appreciated.

Butch in crisis.

---

### Post by bfmetcalf on 2012-03-28
Have you tried just letting the live cd wipe the partitions in the installer?

---

### Post by ButchButchButch on 2012-03-28
I cant seem to make this machine boot from cd?  That would be great if i could make it happen!!!

---

### Post by QIII on 2012-03-28
Is you password something other than your login password?

Is it set to do so in the BIOS/EFI?  Is the optical drive functional?

If you boot to the hard drive, you can't use gparted on it to clear everything anyway since it is mounted at some point.

---

### Post by bfmetcalf on 2012-03-28
If you can't get the cd to boot.  You can also try the USB option as well.  and +1 for checking the BIOS.

---

### Post by rmil on 2012-03-28
It sounds unusual but try ubuntu server live cd recovery. It has really good options for system recovery You can use several variants of shell approach.

---

### Post by forrestcupp on 2012-03-28
Like others said, you can change the boot order in the BIOS. But also, most computers have a boot menu where you can choose what device to boot from without changing the BIOS. As soon as you turn your computer on, it should tell you some key to press for the BIOS, and another key for the Boot menu. If your computer has that, you should be able to choose to boot from your CD drive and boot to the Live CD.

You can partition your drive from the installation. There's no reason to waste your time doing it before hand. And if you're going to do a clean install, you're going to have to figure out how to boot from your CD or USB anyway. So you might as well just wait and partition from the installation.

---

### Post by ButchButchButch on 2012-03-28
I am looking now for the sony boot menu options. Ubuntu bios only shows
ubuntu
ubuntu recovery
memory test x2.
back in a moment. and thanks all for the help!!

---

### Post by ButchButchButch on 2012-03-28
Well This situation has been resolved by running my ubuntu 9.0.4 disk. installed without a hitch and will upgrade from here. Thank you all for the help!!!!

---

### Post by jerome1232 on 2012-03-28
I realize your issue has been resolved, but I wanted to note when you get that error in recovery mode, it's because your / is mounted read only, to correct that run

```
mount -o remount,rw /
passwd username
reboot
```

---

