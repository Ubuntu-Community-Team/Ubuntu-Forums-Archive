---
title: "mounted partitions on desktop as icons"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Jeenyus on 2008-08-10
I have 2 partitions (Windows XP and a shared FAT32) that I have set to automatically mount on boot.  However I don't like that they show up on my desktop as icons, is there a way to still have them mount automatically without showing up as icons on the desktop?

Thank you

---

### Post by Vivaldi Gloria on 2008-08-10
> **Jeenyus said:**
> I have 2 partitions (Windows XP and a shared FAT32) that I have set to automatically mount on boot.  However I don't like that they show up on my desktop as icons, is there a way to still have them mount automatically without showing up as icons on the desktop?

Thank you

Mount them to /mnt/mountpoint in fstab. First create the folders in /mnt. Then modify fstab. Then restart.

They wont make desktop icons. You can symlink them where ever you want.

---

### Post by SZ07 on 2008-08-10
Here is another way:

Open up the gnome Configuration Editor. Expand apps and then nautilus. Click on desktop and, in the pane on the right, uncheck volumes_visible.

---

### Post by Vivaldi Gloria on 2008-08-11
> **SZ07 said:**
> Open up the gnome Configuration Editor. Expand apps and then nautilus. Click on desktop and, in the pane on the right, uncheck volumes_visible.

That's possible but it also stops usb disks and cd-roms to appear on the desktop.

---

### Post by !ndy on 2008-08-11
i've saved this super console trick, so i can try to impress people with it ;-)

```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

it's for the /media/disk/ icon...

---

