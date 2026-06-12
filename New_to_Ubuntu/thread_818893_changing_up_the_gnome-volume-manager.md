---
title: "changing up the gnome-volume-manager"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-06-04
On my fstab I have my second data partition mounting at /mnt/datadisk on bootup.  I'd like to have a link to this partition on my desktop.
I know that if I have it mount in /media/datadisk it will show up as a volume on the desktop (however mounted partitions should properly go in /mnt).
Does anyone know how to tell the gnome-volume-manager where to look for mounted devices?
```
# /dev/hda2
UUID=b3b801c3-3c82-440a-ac2a-1d1cb4f51c94 /mnt/datadisk   ext2    relatime        0       2

```

---

### Post by tom56 on 2008-06-07
I'm not sure that /mnt is really used any more. Certainly, as you say, most things are mounted to /media. Why not just mount it to /media if it works?

---

### Post by quelx on 2008-06-07
I don't think you want to change volume-manager's behaviour.  Any usb drives you add will no longer show up if you change the path it looks for them.  Since the drive is permanently mounted create a symlink at the **terminal**.
```
ln -s /mnt/datadisk ~/Desktop/datadisk
```

---

