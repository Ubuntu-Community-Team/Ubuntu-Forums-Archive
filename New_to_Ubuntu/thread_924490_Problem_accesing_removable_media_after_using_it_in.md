---
title: "Problem accesing removable media after using it in ubuntu"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Macdelaney on 2008-09-19
After i downloaded the pics from my family's camera, everytime i try to do that in a windows pc a error message pop's up saying that i have no permissions. Could ubuntu have changed the permissions so i'm the only one who can access it? Any idea on how to change it back?

---

### Post by oilchangeguy on 2008-09-19
> **Macdelaney said:**
> After i downloaded the pics from my family's camera, everytime i try to do that in a windows pc a error message pop's up saying that i have no permissions. Could ubuntu have changed the permissions so i'm the only one who can access it? Any idea on how to change it back?

in ubuntu are you either unmounting the camera, or turning off the computer before you unplug the camera?

---

### Post by Delirium_Trigger on 2008-09-19
> **oilchangeguy said:**
> in ubuntu are you either unmounting the camera, or turning off the computer before you unplug the camera?

I used to have a similar problem with an external hard drive.
You have to always make sure you unmount the camera.
When switching back to Windows make sure you "Safely Remove Hardware" which is the same thing as unmounting.

---

### Post by SarahKH on 2008-09-19
> **Macdelaney said:**
> After i downloaded the pics from my family's camera, everytime i try to do that in a windows pc a error message pop's up saying that i have no permissions. Could ubuntu have changed the permissions so i'm the only one who can access it? Any idea on how to change it back?

Unlikley, most memory cards are FAT32 formatted, which doesn't understand the advanced permissions bits of either a *NIX file system or NTFS. 

What's probably happening is the system isn't cleanly unmounting the camera, make sure you select eject (or unmount) from the right click menu and leave it a few seconds after the icon vanishes; sometimes a little bubble appears telling you its writing data and finally that it's safe to remove.  Sometimes this box doesn't however generally speaking,  leaving it a little while will do the same thing if the bubbles don't appear.

---

