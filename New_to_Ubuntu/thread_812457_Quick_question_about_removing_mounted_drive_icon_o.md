---
title: "Quick question about removing mounted drive icon on desktop"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by alwiap on 2008-05-29
Hi,

I've done it before but forgot, but how do I remove the icons on my Gnome desktop of my mounted drives?  I would like to have a clean desktop, and I know it can be done, my search didn't find anything.  Thanks!

---

### Post by drs305 on 2008-05-29
> **alwiap said:**
> Hi,

how do I remove the icons on my Gnome desktop of my mounted drives? 

To hide the volumes:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

To show them again, reset value to 'true'.

---

### Post by unutbu on 2008-05-29
Right-click on the icon and then select 'move to trash'.

---

### Post by alwiap on 2008-05-29
> **drs305 said:**
> To hide the volumes:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

To show them again, reset value to 'true'.

thank you very much! just what i needed.  100 internets to you.

---

### Post by iaculallad on 2008-05-29
> **alwiap said:**
> Hi,

I've done it before but forgot, but how do I remove the icons on my Gnome desktop of my mounted drives?  I would like to have a clean desktop, and I know it can be done, my search didn't find anything.  Thanks!

Press Alt+F2, then type gconf-editor and enter. Browse to Apps->Nautilus->Desktop, search for "volumes_visible" in the right-hand pane of your window and uncheck it.

---

### Post by gabdullah on 2009-01-04
drs305 and iaculallad are both right.

---

### Post by Elssha on 2009-05-07
> **drs305 said:**
> To hide the volumes:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

To show them again, reset value to 'true'.

how about if i want my hard drive partitions to not show up, but discs and usb media to pop up? Or just a specific drive? Is there a way to differentiate or are we stuck with an all or nothing? 
Thanks a bunch, 
Elssha

---

### Post by drs305 on 2009-05-07
> **Elssha said:**
> how about if i want my hard drive partitions to not show up, but discs and usb media to pop up? Or just a specific drive? Is there a way to differentiate or are we stuck with an all or nothing? 
Thanks a bunch, 
Elssha

Elssha,

There is a way, but you will have to edit /etc/fstab. Showing volumes (which is what the windows manager, calls them) is an 'all-or-nothing' proposition. Any partition mounted in /media will be displayed if the setting is enabled. You *can* hide the hard drives by moving the mount point to /mnt or some other folder. Partitions not mounted in /media won't be shown on the Desktop by default. *They also will not be shown in Nautilus' Places, you will have to make a shortcut for them.*

To change the mount point, you would make a new mount point in /mnt, make yourself the owner (for ext3/4) and edit /etc/fstab to change the mount point, then remount them. I'll use /media/storage as the current mount point for this example. You would substitute the name of your /media/ folder course for 'storage':
```

mkdir /mnt/storage
sudo chown -R *yourusername:* /mnt/storage
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```
Change the mount point in the fstab line. Leave everything else as it is:
> UUID=XXX-XX-XXX-XXXXXX  /**[COLOR="DarkRed"]mnt[/COLOR]**/storage  ext3 defaults 0 2 
Unmount and mount the fstab entries. Disregard the "busy" messages:
```
sudo umount -a
sudo mount -a
```
The partition should now be mounted on /mnt/storage and no longer be on your Desktop.

---

### Post by Ms_Angel_D on 2009-05-07
Just a bit of FYI [Ubuntu-Tweak]("http://ubuntu-tweak.com") gives you the option to hide/show mounted drives on the desktop.

---

### Post by mjcritchie on 2010-02-05
> **drs305 said:**
> Elssha,

There is a way, but you will have to edit /etc/fstab. Showing volumes (which is what the windows manager, calls them) is an 'all-or-nothing' proposition. Any partition mounted in /media will be displayed if the setting is enabled. You *can* hide the hard drives by moving the mount point to /mnt or some other folder. Partitions not mounted in /media won't be shown on the Desktop by default. *They also will not be shown in Nautilus' Places, you will have to make a shortcut for them.*

To change the mount point, you would make a new mount point in /mnt, make yourself the owner (for ext3/4) and edit /etc/fstab to change the mount point, then remount them. I'll use /media/storage as the current mount point for this example. You would substitute the name of your /media/ folder course for 'storage':
```

mkdir /mnt/storage
sudo chown -R *yourusername:* /mnt/storage
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```
Change the mount point in the fstab line. Leave everything else as it is:

Unmount and mount the fstab entries. Disregard the "busy" messages:
```
sudo umount -a
sudo mount -a
```
The partition should now be mounted on /mnt/storage and no longer be on your Desktop.

This worked a treat for me, although I had some problems with the 'storage' folder I created not being capitalised to match the name of my storage partition. So I ended up renaming the /mnt/storage file to /mnt/Storage

Thanks for posting :)

---

### Post by HuckBerry on 2010-02-22
I've used this trick for a long time, however after updating to 9.10 (clean install) it seems to no longer work.  I have double checked that /apps/nautilus/desktop/volumes_visible is unchecked in gconf-editor.

---

