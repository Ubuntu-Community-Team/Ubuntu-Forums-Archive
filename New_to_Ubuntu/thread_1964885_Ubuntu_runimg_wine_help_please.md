---
title: "Ubuntu runimg wine help please"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by boss300 on 2012-04-24
ok so whene im in wine i need to be able to mount my allready munted devices such as usb devices or hardrive. how do I mount them? withen the command prompt wine ships with?

oh auto mount would be nice for mounting what ever is in the media folder thanks :0

sorry for my bad grammer! :(

---

### Post by anewguy on 2012-04-24
You can't use USB devices other than your keyboard, mouse and maybe printer in wine.  Wine doesn't support USB.

---

### Post by boss300 on 2012-04-24
> **anewguy said:**
> You can't use USB devices other than your keyboard, mouse and maybe printer in wine.  Wine doesn't support USB.

i have found mounted devices in regedit.

---

### Post by 3rdalbum on 2012-04-24
> **boss300 said:**
> ok so whene im in wine i need to be able to mount my allready munted devices such as usb devices or hardrive. how do I mount them? withen the command prompt wine ships with?

oh auto mount would be nice for mounting what ever is in the media folder thanks :0

sorry for my bad grammer! :(

In Wine, you'll find a "Z" drive. This actually contains the contents of your / partition from Ubuntu. Any mounted drives on Ubuntu will therefore appear somewhere in the Z drive; for instance, USB storage will appear in Z:\media, and mounted network shares will appear in Z:\home\(username)\.gvfs\

Basically, wherever it mounts in Ubuntu, it's present in the Z drive in Wine.

You don't "mount" the device a second time.

The devices you can see mounted in Regedit are the default Wine ones (C, D, and Z). DO NOT MESS WITH THESE IN REGEDIT.

---

### Post by anewguy on 2012-04-25
interesting if this works - wine still claims no USB support.

Dave ;)

---

