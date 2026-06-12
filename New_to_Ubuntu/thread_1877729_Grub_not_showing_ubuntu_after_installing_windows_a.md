---
title: "Grub not showing ubuntu after installing windows and restoring grub"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by arpit22x on 2011-11-08
Dear ones,

NewBee here, Please help.

I had ubuntu previously. I installed windows 8 developer preview and reinstalled grub 2 using 'boot-repair' but its not showing ubuntu in the list. The info about grub installation is in the following link. Pls tell me what mistake I did.

[http://paste.ubuntu.com/732297/](http://paste.ubuntu.com/732297/) 

I'll appreciate any help.

Arpit

---

### Post by drs305 on 2011-11-08
The Grub 2 files were installed on sda1 and not on sda2, your Ubuntu partition.

You can install Grub 2 to the correct location from the LiveCD. Boot the CD, then from the Desktop open a terminal and mount your Ubuntu partition with the first command. Install Grub 2 with the second - do not use the partition number in the second command:

```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /dev/sda2
```

When you reboot, you will get a grub rescue prompt, since it won't find the grub.cfg file (which isn't created with the above commands).

To boot, try running these commands from the grub prompt:
```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
insmod linux
linux (hd0,2)/vmlinuz root=(hd0,2) ro
initrd (hd0,2)/initrd.img
boot
```

Once you can boot into Ubuntu, run the following to generate the Grub 2 menu:```

sudo update-grub
```

If the boot commands don't work, you can use the LiveCD to accomplish the second part of the above (to produce a working Grub 2 menu)  by 'chrooting' and running 'update-grub' from the 'chroot'. The link on how to do this is in the 'Chroot' link in my signature line.

---

