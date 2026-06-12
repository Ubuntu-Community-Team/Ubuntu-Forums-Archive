---
title: "Dmesg, path of connected usb drive"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by bryan21 on 2015-01-03
how do I find the path of connected usb drive, I tried using dmesg | grep -i usb but I get a lot of stuff and I don't understand please help me.

---

### Post by DuckHook on 2015-01-03
Not sure I understand. Do you mean the file path? If so, then just look in *Nautilus*. If you hover the mouse pointer over the drive, the path will appear in a pop-up. Alternatively, right click the drive and select "properties", the path will show up in the information box. On most distros, it will be under /media/. If only using command line, then the best is *df*. This shows both device path and file path. Example:```
...
/dev/sdg1     3865264     28428     3640488     1%     /media/duckhook/usb_drive
```The first reference is the device path. The last is the file path. Most users will only be interested in the file path. Multiple USB drives will appear on their own line.

---

### Post by nerdtron on 2015-01-03
If the device is already mounted you can also use any following commands. (especially helpful if you already know how big the usb capacity is)

```
lsblk
mount -l
df -h

```

Then you can use grep is you need a particular line.

---

