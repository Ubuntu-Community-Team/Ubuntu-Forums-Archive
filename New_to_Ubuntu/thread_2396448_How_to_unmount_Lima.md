---
title: "How to unmount Lima"
date: 2018-07-16
forum: New to Ubuntu
---

### Post by Odense on 2018-07-16
Ubuntu 16.04 LTS with classic gnome desktop.

I have previously needed help to remove a config lock from Lima - now I need to unmount so I can mount it again (if there is no "remount" option.
If it was "really" mounted How do I i should be able to use "Lima start" and "Lima login" but it must be onle "semi-mounted"?

---

### Post by Holger_Gehrke on 2018-07-16
Read the error message again, carefully. The Lima-app wants to mount the contents of the Lima-device into the directory '/home/morten/Lima/', but doesn't do so because there's some files in there. Normally Linux does not care about files in directories used as mount points (they become inaccessible for the duration of the mount), but the Lima-app seems to do it differently. Check the directory contents and either move those files somewhere else or erase them.

Holger

---

### Post by Odense on 2018-07-16
Thank you Holger - that solved it :-)

---

