---
title: "Uninstalling Kubuntu"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by sqrooup on 2008-11-19
I have a duel-boot Ubuntu/Kubuntu system, on 2 separate hard drives, the master set up as Ubuntu 8.10, the secondary Kubuntu 8.04, which was installed after the Ubuntu.

I prefer the Ubuntu, but the Kubuntu is now the first option on turning on the PC, the screen resolution will not go beyond 800 x 600, and I cannot find the update option.

I have decided to stick with Ubuntu, so what is the best way to remove Kubuntu?

---

### Post by nhasian on 2008-11-19
since the ubuntu filesystem is on your primary hard disk, you should just be able to wipe the drive with Kubuntu on it.  you could use gparted to format the drive again or you can just delete all the files from it.  also you'll need to edit the grub menu to remove the kubuntu and make Ubuntu the default booting option.

---

### Post by caljohnsmith on 2008-11-19
Since you installed Kubuntu after Ubuntu, most likely Kubuntu controls the MBR (Master Boot Record) of your boot drive and is thus in charge of your booting; if you simply wipe Kubuntu off the HDD, you won't be able to boot after that. To fix it, you can reinstall Grub to the MBR so that Ubuntu is back in charge of the booting process. So once you delete Kubuntu, you'll need to open a terminal from the Live CD (Applications > Accessories > Terminal) and do the following to reinstall Grub:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And then you should be all set. Let me know how it goes or if you run into problems. :)

---

### Post by Keen101 on 2008-11-19
I'd just say wipe the kubuntu drive with gparted
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then use the Super Grub Disk to restore GRUB. The disk should restore the grub menu that was on the first drive, and no more kubuntu options should be present. Should be quick and easy.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

