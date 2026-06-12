---
title: "Errors"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by arashispencer on 2008-06-20
I have error 15,17 and 21 different error each time I restart after the kubuntu installation:(. And now I'm desperately in need for someone to guide me.... I'm a total new kubuntu user...
I never change any setting in between restarts.

1st hdd = win with few partitions (doc, media, installer...)
2nd hdd = kubuntu (Bought a new one just to learn it. It's an external USB hdd though)

I'm unable to enter fdisk (to windows) to edit the boot, & I definitely know nothing about kubuntu boot loader.

Can't even log in to windows even with the ext hdd detached.

I've followed the steps in "grub error 21 windows xp" posted by dennycraig but my terminal can't seem to find anything and my results are nowhere near......

---

### Post by Dynaflow on 2008-06-20
If you have an Ubuntu (or really any other Linux) LiveCD lying around, you can boot that that and edit GRUB from within its desktop.  Just boot into the LiveCD, get to a desktop, open a terminal, and input

```
gksudo gedit /boot/grub/menu.lst
```

You can also use [Super GRUB Disk]("http://www.supergrubdisk.org/") to fix a thoroughly FUBAR'ed GRUB.

However, first look to make sure you don't have anything like flash drives, portable hard drives, or anything else that something, somewhere might interpret as a new hard drive.

I get GRUB error 17 all the time when I forget to unplug my portable hard drive from my ancient HP, whose BIOS can't deal with such things being plugged in at boot time without interpreting them as internal hard drives, which seems to throw off GRUB from where on the partition table to find certain needful things.

---

### Post by Dedoimedo on 2008-06-20
Hello,

See if my answer in this thread help you:
[http://ubuntuforums.org/showthread.php?t=834190](http://ubuntuforums.org/showthread.php?t=834190)

Dedoimedo

---

### Post by arashispencer on 2009-09-10
tnx dynaflow,tried unpluggin unused hdd,same...
tnx dedoimedo...i was unable 2 bypass d error 21 unles i reboot more than 4-5 times...bt it was a full installation on a new usb hd...wil keep tryin though...

---

