---
title: "reinstalling windows."
date: 2008-07-17
forum: New to Ubuntu
---

### Post by appi2012 on 2008-07-17
I installed ubuntu a while ago, however the peculiar boot setup involving a HP_Recovery partition caused windows to no longer be bootable. (see [http://ubuntuforums.org/showthread.php?t=844598](http://ubuntuforums.org/showthread.php?t=844598)) The only solution that is left, it seems, is to reinstall windows. However, a quick google search has many links saying how you should always install windows first, and then ubuntu. But I spent a lot of time getting my ubuntu install to work (wireless, sound, etc.) so I really would not like to reinstall it. 

I was hoping there was a way to reinstall windows while keeping ubuntu. Could someone guide me through deleting my bothersome HP_Recovery Partition and my Windows install partition, and then making the ubuntu partition bigger, and finally installing windows xp in the empty space, and reinstalling grub.

---

### Post by benfindlay on 2008-07-17
You can reinstall windows, making sure not to touch your ubuntu partitions. Then the only problem will be that your grub configuration will be messed up. This can then be repaired using an ubuntu live cd, or something like the supergrubdisk.

Hope this helps!

Ben

---

### Post by Inxsible on 2008-07-17
> **appi2012 said:**
> I installed ubuntu a while ago, however the peculiar boot setup involving a HP_Recovery partition caused windows to no longer be bootable. (see [http://ubuntuforums.org/showthread.php?t=844598](http://ubuntuforums.org/showthread.php?t=844598)) The only solution that is left, it seems, is to reinstall windows. However, a quick google search has many links saying how you should always install windows first, and then ubuntu. But I spent a lot of time getting my ubuntu install to work (wireless, sound, etc.) so I really would not like to reinstall it. 

I was hoping there was a way to reinstall windows while keeping ubuntu. Could someone guide me through deleting my bothersome HP_Recovery Partition and my Windows install partition, and then making the ubuntu partition bigger, and finally installing windows xp in the empty space, and reinstalling grub.
1) Install XP - the way you normally would - just make sure you dont over-write Ubuntu :)
2) Get Super grub disk and then use that to install grub again. Only after you do this will you be able to access Ubuntu again.

---

### Post by appi2012 on 2008-07-17
How exactly would I use super grub disk or the live cd to set up grub again?

---

### Post by OffAxis on 2008-07-17
super grub disc is the easiest.
It'll boot and ask you a question ("Do you want to fix grub?")
-"yes."
and that's it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

