---
title: "HOWTO: Formatting and partitioning your external usb hard drive"
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jordilin on 2006-07-27
So, you have just bought a brand new external usb hard drive where you’ll store your backup data. Well, then now the question. How I format my new external usb hard drive using Ubuntu Linux or any tool available in the Linux world? In Ubuntu, there are two tools that aim to format and partition your hard drive which are Gparted and Qparted. Both of them nearly equal, so I’m going to introduce you to Gparted and afterwards DiskDrake

**GPARTED**

Using Gparted with an installed Ubuntu Os is quite difficult and buggy because your external hard drive must be unmounted and Ubuntu mounts it automatically. The best way to do it is using the Gparted live cd which can be found in:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It starts a fluxbox window manager with Gparted launched automatically. Then you can very easily format and partition your external usb hard drive. Your external hard drive will always be in /dev/sdaX.
[B]
DISKDRAKE[/B]

You can use DiskDrake with another live cd, but in this case a Linux Os live cd such as PCLinuxOS which can be downloaded from:

[http://www.pclinuxos.com/news.php](http://www.pclinuxos.com/news.php)

Once you download the image, burn it, and boot from it. Enter the OS with user=root and password=root. It will go into a KDE Desktop. Open the K menu and run the command diskdrake. The DiskDrake partition editor will pop up. Then, there you are. It’s very easy to use. Partition and format your hard drive as you want.
[B]
VOLUME LABELS?[/B]

With the apps pointed out, you will not be able to add labels (volume), but don’t worry, the linux command line is here to help us. Just once you have formatted your hard drive type:
```

df -k
```

and some lines will appear such us:
```

/dev/sda5 100789972 131232 95538828 1% /media/usbdisk
```

You see that Ubuntu automatically mounts the formatted harddrive with the generic label usbdisk. But you want an specific name. Then type:

```

e2label /dev/sda5 nameofthelabel
```

Once done, unmount the hard drive and plug it in again. Ubuntu will mount automatically the hard drive and a folder with the name of nameoflabel will appear in your desktop. Another issue. Most probably, Ubuntu will mount the hard drive with root permissions. To change the permissions, so you can write in your hard drive change them by writing this:

```
chown yourusername:yourgroupname /media/nameofthelabel
```

---

### Post by Carrots171 on 2007-01-06
Thanks for the HOWTO - I just got an external hard drive and I couldn't have set it up without this guide. One small error, though: shouldn't *chown yourusername:yourgroupname /media/nameofthelabel* be *sudo chown yourusername:yourgroupname /media/nameofthelabe*l?

---

### Post by jordilin on 2007-01-06
> **Carrots171 said:**
> Thanks for the HOWTO - I just got an external hard drive and I couldn't have set it up without this guide. One small error, though: shouldn't *chown yourusername:yourgroupname /media/nameofthelabel* be *sudo chown yourusername:yourgroupname /media/nameofthelabe*l?

Yes, you are right. Most probably you'll need the sudo command. Thanks

---

