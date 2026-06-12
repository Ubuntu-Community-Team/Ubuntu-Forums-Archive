---
title: "[SOLVED] Getting Rid of Drive Icon from Desktop?"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-10-23
I recently added a small, second hard drive to my box.  I modified fstab so that it currently mounts as a subdirectory off my home directory.  (The ultimate goal is to use the drive as the /home partition, but for the mean time I am using it as additional storage.)

Now, when I boot up, I get an icon (pic attached) on the desktop for the drive itself.  Clicking on it takes me to its mount point in my /home directory.  I don't want that icon on my desktop and there seems to be no obvious way to remove it.  How does one get rid of it without loosing the fstab mounting to my /home directory?

---

### Post by drs305 on 2008-10-23
You can run the following to prevent volumes (partitions) from showing on your desktop:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

You can view them again by changing the setting back to 'true'.

You can also make the same changes by opening gconf-editor and making changes in the gui:
```
gconf-editor /apps/nautilus/desktop
```

This is also where you can hide/display your trash bin icon, etc.

---

### Post by jerome1232 on 2008-10-23
edit: Seems I was beaten to it by drs305 :D

Changing this setting in gconf should do it.

Alt+f2, type gconf-editor, Expand apps in the left hand pane, find nautilus and expand that in the left hand pane, now select desktop.

In the right hand pane there should be an option called 'volume visible' try unchecking that.

---

### Post by H.Callahan on 2008-10-23
> **drs305 said:**
> You can run the following to prevent volumes (partitions) from showing on your desktop:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

You can view them again by changing the setting back to 'true'.

You can also make the same changes by opening gconf-editor and making changes in the gui:
```
gconf-editor /apps/nautilus/desktop
```

This is also where you can hide/display your trash bin icon, etc.
But won't that make all volumes disappear?  I want removable media like a flash drive to show up -- just not this one since it is hooked up internally via the IDE channel.

---

### Post by jerome1232 on 2008-10-23
Then try mounting it under /mnt, and placing a symlink in your ~/ to it.

example code for create a symlink to /mnt in your ~/  labeled as 'data'

```
ln -s /mnt ~/data
```

---

### Post by drs305 on 2008-10-23
> **H.Callahan said:**
> But won't that make all volumes disappear?  I want removable media like a flash drive to show up -- just not this one since it is hooked up internally via the IDE channel.

Yes, it would hide all drives. As jerome mentions, if you mount it in /mnt instead of /media it won't display on the desktop. If you choose to go this route, you must make a mountpoint in /mnt and you will probably want to change the ownership of the mountpoint to yourself:
```

sudo mkdir /mnt/mountpoint
sudo chown -R yourusername: /mnt/mountpoint
chmod -R 750 /mnt/mountpoint

```

---

### Post by H.Callahan on 2008-10-23
Ok...a little confused here.

I don't have it mounted under /media.  I have it mounted under /home/*username*/downloads via fstabs, not under /media.  My /media directory looks like this:
```
drwxr-xr-x  5 root root 4096 2008-10-22 16:20 .
drwxrwxrwx 21 root root 4096 2008-10-18 17:38 ..
lrwxrwxrwx  1 root root    6 2008-04-22 15:41 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-04-22 15:41 cdrom0
drwxr-xr-x  2 root root 4096 2008-04-22 15:41 cdrom1
lrwxrwxrwx  1 root root    7 2008-04-22 15:41 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2008-04-22 15:41 floppy0
-rw-r--r--  1 root root    0 2008-10-22 16:20 .hal-mtab

```
Looking at the properties of the icon, it shows its mount point as being /home/*username*/downloads.  It also shows up under /dev as sdb (I assume the drive) and sdb1 (I assume the partition).

---

### Post by jerome1232 on 2008-10-23
Yeah I wouldn't have thought that things mounted at ~/ would be shown on your desktop, but I just tested it and they are.

That's why I suggested the symlink

---

### Post by H.Callahan on 2008-10-23
Ok, after straightening out some permission problems (Fumble Fingers strikes again!), that seems to have worked.  Not quite as elegant as just mounting in fstab, but it does work and is visible/usable by a Windows station on the network.

Thanks all!

Oh, BTW, what are the default permissions for a home directory?  750?  770? 644? 744?

---

### Post by jerome1232 on 2008-10-23
mines: dwrxr-xr-x, in numbers that's what 755?

And I haven't changed them so I assume that's default.

---

### Post by H.Callahan on 2008-10-23
Yup, that would be 755...

Thanks again!

---

