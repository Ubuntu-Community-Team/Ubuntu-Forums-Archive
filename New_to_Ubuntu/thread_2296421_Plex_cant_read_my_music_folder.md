---
title: "Plex cant read my music folder"
date: 2015-09-25
forum: New to Ubuntu
---

### Post by ruvapost on 2015-09-25
Removed Windows and installed Ubuntu. Then I install Plex and point the musik libary to my home music-folder. Cant read anyting, Plex say. Then I point it to home/me/Muic/Plex Music. Can´t I have folders strukture in Linux with Plex?

---

### Post by TheFu on 2015-09-25
a) use complete, full, paths to the top level. That must start with a /
b) check file ad directory permissions - if the "plex" userid cannot read the files, then plex cannot either.

---

### Post by ruvapost on 2015-09-26
> **TheFu said:**
> a) use complete, full, paths to the top level. That must start with a /
Yes I do thath and it works in home folder (Music/Plex Music)
> **TheFu said:**
> b) check file ad directory permissions - if the "plex" userid cannot read the files, then plex cannot either.
Done that on second hardisk ssd "SATA Ext4" and Plex in Ubuntu can´t read it (LVM disks Lager/Share) but KODI can read from Windows/Android/Ubunut-Mate from the network.

---

### Post by TheFu on 2015-09-26
Proof?  
**ls -al**

---

