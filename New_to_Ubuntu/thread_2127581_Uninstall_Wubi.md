---
title: "Uninstall Wubi?"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by Koneke on 2013-03-20
Just to make sure, is it entirely safe to just uninstall Wubi after  migrating? I managed to migrate succesfully quite a while back, but I  just found my old Wubi install lying about taking up space. No risk that  the uninstallation would poke the new install in any way?

---

### Post by woxuxow on 2013-03-20
if you unistall wubi the ubuntu that is installed by wubi will be removed
if you installed a ubuntu with wubi and after that installed another one
uninstalling wubi have no effect on your new installed ubuntu and grub menu

just make sure there is no Useful data on the ubuntu you want to remove, after removing wubi it would be hard(almost Impossible) to recover it

---

### Post by bcbc on 2013-03-20
> **Koneke said:**
> Just to make sure, is it entirely safe to just uninstall Wubi after  migrating? I managed to migrate succesfully quite a while back, but I  just found my old Wubi install lying about taking up space. No risk that  the uninstallation would poke the new install in any way?
Provided you installed grub when you migrated, it should be safe.

So, when you boot, the first menu you see is the Grub menu (Ubuntu first option). When you select Windows, you then get the Windows boot manager with Windows and Ubuntu (the Wubi one). If that's correct, then your migrated install does not rely on any aspect of Wubi anymore and uninstalling is fine.

Also to check you are running the real install:
```
bcbc@13:47:04:~$ mount | grep ' / '
/dev/sda8 on / type ext4 (rw,errors=remount-ro)

```
If instead it says the following, you are booting the Wubi install:
```
bcbc@13:47:04:~$ mount | grep ' / '
/dev/loop0 on / type ext4 (rw,errors=remount-ro)

```

---

### Post by dolphin194 on 2013-03-21
If you uninstall Wubi, your new installation will not be harmed.

---

