---
title: "i have problem in booting ubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by yuva3d on 2008-05-27
i have problem in booting ubuntu,
b4 i have windowsxp in my c drive after that i install ubuntu 8.04 (in the d driver but i did't formated the D drive) it was install great and i have dual booting. after i formated the c drive and install windows sp again now i not can't able to boot in to ubuntu the gurb booter is not happing can any one pls help me how to get back same boot loder again...

---

### Post by billgoldberg on 2008-05-27
> **yuva3d said:**
> i have problem in booting ubuntu,
b4 i have windowsxp in my c drive after that i install ubuntu 8.04 it was install great and i have dual booting. after i formated the c drive and install windows sp again now i not can't able to boot in to ubuntu the gurb booter is not happing can any one pls help me how to get back same boot loder again...

Windows has the nasty habit of over writing the boot loader.

You'll need to reinstall the grub and then you'll be able to boot windows and ubuntu.

The easiest way to do this is by using the "super grub disk".

link:
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

But it can also be done from an ubuntu live cd.

link:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by lisati on 2008-05-27
The standard wisdom is to install Windows first. If for some reason you've installed Ubuntu before Windows, you'll need to do a bit of tinkering.

Try searching the forums for "Supergrub".

---

### Post by housam on 2008-05-27
> **yuva3d said:**
> i have problem in booting ubuntu,
b4 i have windowsxp in my c drive after that i install ubuntu 8.04 (in the d driver but i did't formated the D drive) it was install great and i have dual booting. after i formated the c drive and install windows sp again now i not can't able to boot in to ubuntu the gurb booter is not happing can any one pls help me how to get back same boot loder again...

[[COLOR="Red"]_Recover grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") after installing windows

---

