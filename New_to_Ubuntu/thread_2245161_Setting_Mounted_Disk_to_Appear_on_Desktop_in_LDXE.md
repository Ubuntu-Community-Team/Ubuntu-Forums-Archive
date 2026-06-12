---
title: "Setting Mounted Disk to Appear on Desktop in LDXE"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by Henry_Flower on 2014-09-21
I really liked the way a mounted disk would appear on the desktop when plugged in in Linux Mint and I'd like to duplicate it in lubuntu. I've seen some guides on how to do this in Unity via gsettings in the terminal but the command is not the same for LDXE and I'm not experienced enough in linux to make the adjustment myself.  Thanks.

EDIT: easy to fix. see first reply. thanks!

---

### Post by ajgreeny on 2014-09-21
Go to Desktop preferences and select "Go to connected volumes on the desktop"

---

### Post by bab1 on 2014-09-21
> **Henry_Flower said:**
> I really liked the way a mounted disk would appear on the desktop when plugged in in Linux Mint and I'd like to duplicate it in lubuntu. I've seen some guides on how to do this in Unity via gsettings in the terminal but the command is not the same for LDXE and I'm not experienced enough in linux to make the adjustment myself.  Thanks.
I've just installed Lubuntu 14.04 yesterday, so the install is at all the defaults.  I have no problems seeing the FAT and NTFS volumes showing up on my desktop when I insert them.  These are mounted at */media/<myusername>/<blkid or disk label>*.

How are you mounting these volumes and what is the file system format (i.e. FAT, NTFS or EXT)?

[COLOR="#0000FF"]Edit:  "Go to Desktop preferences and select "show connected volumes on the desktop"

Of course! [/COLOR]

---

