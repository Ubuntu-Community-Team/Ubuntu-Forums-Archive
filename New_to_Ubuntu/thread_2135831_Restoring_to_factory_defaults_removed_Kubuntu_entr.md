---
title: "Restoring to factory defaults removed Kubuntu entry on Windows Boot Manager"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by vgezer on 2013-04-15
I got my laptop repaired by service and they restored everything to factory defaults. Now, I cannot access my kubuntu from "Windows Boot Manager". I had my kubuntu installed via WUBI on D drive and fortunately, they did not touch that drive. 

I created a bootable kubuntu image on my flashdisk and tried to install again, but it seems it will make a fresh install over my kubuntu.

---

### Post by bcbc on 2013-04-15
Move D:\ubuntu to D:\ubuntubackup  (rename folder).
Reinstall on D: choosing the smallest install size (5GB)
Replace the D:\ubuntu\disks folder with the backup you made

Reboot.

That's if you want to keep using Wubi. There are other options if you want to replace D: with a linux partition and migrate your kubuntu to it.

---

### Post by vgezer on 2013-04-15
great. how couldn't I think about this :). thanks a lot.

---

