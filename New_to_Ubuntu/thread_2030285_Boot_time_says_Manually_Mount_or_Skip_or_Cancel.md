---
title: "Boot time says Manually Mount or Skip or Cancel"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-07-20
I have a usb flash (or thumb or jump) drive inserted into a usb port. It was not mounted as /media, so that I could run executable objects on it (under Linux). By accident I damaged the device by removing it while the 'puter was powered up.

When I cold (or warm) boot, I receive a (probably from GRUB) boot time message about the drive is not mounted and do I want to Skip mounting, Manually mount or cancel the boot.

From their, selecting Manual brings up the terminal. What commands do I use to mount this device?

I have to ask this, as the device, while inserted does NOT show up in either lsusb or /media ls - it's a goner!

So, if the device hasn't been fried, anybody got a clue as to how to mount a ghost device?

---

### Post by drs305 on 2012-07-20
Have you checked the fstab file to see if the drive is listed therein? If it is, simply removing the entry (or placing a # symbol at the start of the line) will remove the boot message.

Use the editor of your choice as root (gksu for graphical apps, sudo for non-GUI):
```
sudo nano /etc/fstab
```

---

### Post by NikTh on 2012-07-20
Hi , 
maybe its a problem with UUID . 
Post the results of these 2 commands
```
cat /etc/fstab
sudo blkid
``` 

**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane.**
Thanks

---

### Post by Mark_in_Hollywood on 2012-07-20
Strangely enough, the device was nothing more than umounted and by issuing the mount, it came back to life, good as new. (well, I haven't re-booted) but YEA Linux!

---

