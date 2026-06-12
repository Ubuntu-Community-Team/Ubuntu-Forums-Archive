---
title: "Copying Ubuntu from One Partition to Another"
date: 2007-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Irony on 2007-04-21
To copy your distro to another partition or to back it up to an external drive use the following command;

```
sudo cp -axv /. /media/usb/01092010/.
```

To see what the arguments mean type;

```
cp --help
```

Thus in the above example I would boot into Ubuntu as normal and then plug in my usb drive which is already formatted to ext4 and has a label of usb. I already have a bunch of files saved on that drive so I create a folder in the usual fashion (right click and choose Create Folder) - I name the folder according to the date, thus the above example of 01092010 means 1st September 2010.

I then open a terminal and issue the command first shown - this results in an exact copy of my distro to the folder 01092010.

Should I mess up Ubuntu in some manner I can then copy back the back-up from a live CD;

```
sudo cp -axv /media/usb/01092010/. /media/ubuntu/.
```

To do this I would boot up the live CD run **System > Administration > Disk Utility**, format my original Ubuntu partition, then mount that partition and issue the above command.

Its that simple...

[http://shallowsky.com/blog/linux/install/upgrading-without-risk.html](http://shallowsky.com/blog/linux/install/upgrading-without-risk.html)

---

### Post by diwas on 2008-08-14
Thank you...i have to test it out!!

---

### Post by jnw222 on 2008-08-14
use partimage

---

### Post by Irony on 2009-05-24
To edit etc/fstab in the new install open up fstab as root;

```
gksudo gedit
```

And then go to my newly copied /etc/fstab file and drag it into the gedit window and change sda3 (or rather its UUID number) to sda6. To find the new UUID number do;

```
sudo blkid
```

To update grub I do;

```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo grub-install /dev/sda
sudo update-grub
```

Then I boot to the new install and hopefully it works.

---

### Post by Irony on 2010-03-22
x

---

