---
title: "USB Drive Icon Persists"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by JetSirus on 2008-07-11
I administer a public computer that runs Ubuntu 8.04.  Often people will simply pull out their USB drive without dismounting it and the icon remains on the desktop.  The only way I have been able to get rid of them is to reboot the system.  Is there any fix for this?

---

### Post by ConMan318 on 2008-07-11
Well if it shows up in an 'ls' of the Desktop, you could try forcing removal with
```

sudo rm ~/Desktop/**nameOfDeviceHere** -rf

```

---

### Post by mcduck on 2008-07-11
No, it's not really on the Desktop. You'll find the drive in /media.

This command should force the drive to unmount. (force, because the drive isn't there any more and without the -f option umount would complain about that.)
```
sudo umount -f /media/nameofthedrive
```

---

