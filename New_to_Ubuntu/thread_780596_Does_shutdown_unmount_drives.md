---
title: "Does shutdown unmount drives ?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Scratches on 2008-05-03
If you use the menu option to shutdown the computer, does it unmount removable drives before shutting down?  Or will I lose or corrupt data this way?

Reason I ask, is with the new 8.04, I'm unable to unmount any of my Western Digital USB Passport drives by right clicking on their desktop icons.

Thanks,

Scratches

---

### Post by SunnyRabbiera on 2008-05-03
yeh its usually unmounted during shutdown, I would not worry about it

---

### Post by acelin on 2008-05-03
Yeah its unmounted.

---

### Post by nowshining on 2008-05-03
yes and for ur unmounting problem, it may still show the icon, but it's ummounted or should be and when double-clicking the icon it should auto-mount it.

---

### Post by Scratches on 2008-05-04
I've tested it.  Shutdown DOES NOT safely unmount USB drives before shutting down the computer.  I copied 2 directories to a usb western digital passport, then used the menu shutdown (quit).  After reboot there was no data on the passport drives.

I can't believe this unmount bug isn't hotfixed already.

Scratches

---

### Post by mali2297 on 2008-05-04
Have you tried dismounting the device from the terminal?

First, find the device name by typing
```

mount

```
Say it's /dev/sdb1. Then run
```

sudo umount -v /dev/sdb1

```
Do you get any error messages?

---

### Post by ugm6hr on 2008-05-04
> **Scratches said:**
> If you use the menu option to shutdown the computer, does it unmount removable drives before shutting down?  Or will I lose or corrupt data this way?

Reason I ask, is with the new 8.04, I'm unable to unmount any of my Western Digital USB Passport drives by right clicking on their desktop icons.

Shutdown does usually unmount all drives first.

However, if you can't unmount, then shutdown will not be able to either.

This is bizarre - I've just installed 8.04 (Ubuntu AMD64), and my WD Passport works fine.

Must be Thunar misbehaving in XFCE (I have had similar problems of being unable to unmount with Xubuntu 7.10 on a different machine, which ended up corrupting all my files).

---

### Post by Scratches on 2008-05-04
> **mali2297 said:**
> Have you tried dismounting the device from the terminal?

First, find the device name by typing
```

mount

```
Say it's /dev/sdb1. Then run
```

sudo umount -v /dev/sdb1

```
Do you get any error messages?

I get this,
umount: /media/WD Passport: device is busy

This is a fresh install of xubuntu 8.04

---

### Post by mali2297 on 2008-05-04
Further troubleshooting...

Have you tried disabling Thunar volume manager? 
(Go to *File Manager Preferences -> Advanced* or uninstall the package thunar-volman.)

---

### Post by Whiffle on 2008-05-04
> **Scratches said:**
> I get this,
umount: /media/WD Passport: device is busy

This is a fresh install of xubuntu 8.04

That generally means something is using that directory, ie there is a file open, or a terminal is in that directory.  Try doing

lsof | grep WD 

in terminal.
It should show whats using it.

---

### Post by mgm74 on 2008-10-01
I seem to have the same problem, but with my windows FAT32 particion (mounted in /windows). I moved a file from my linux partition to the windows partition and after rebooting to windows, it was missing.

I may have a shutdown script issue (that could be the reason). The shutdown actually takes too short time.. ~10s and it does not give the type of messages I got used to with Debian. 

I do get the System is shutting down message + a few network related assertion failure and warning. Right after these comes the poweroff.
Perhaps the network card issues generate an error which is not handled.. and the rest of shutdown is not performed (including the unmount).

Any help would be appreciated.. thanks.

---

