---
title: "unmounting usb device"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by blairm on 2008-11-26
Hi,

Since installing Ubuntu Studio I don't get an icon on the desktop when I plug in usb devices eg mp3 player, external hard drive.

In past, I've clicked on the icon and selected unmount there - how do I do it in Studio?

Thanks,

Blair

---

### Post by taurus on 2008-11-26
You can just unmount it from a terminal with the umount command.

```
sudo umount /dev/XXXX
```
Replace the XXXX with the name of the device.  If not sure what it is, you can look at the output of this command.

```
df -h
```

---

### Post by Diabolis on 2008-11-26
Now you can unmount devices through nautilus (nautilus 2.24.1) using the pane on the left.

You can also do it in the command line with:
```
sudo umount /media/"name of device"
```

---

### Post by blairm on 2008-11-26
Thanks for the replies - so quick too! Problem solved.:)

Blair

---

