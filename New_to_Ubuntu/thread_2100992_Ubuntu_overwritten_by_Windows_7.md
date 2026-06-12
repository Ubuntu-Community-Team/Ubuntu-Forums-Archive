---
title: "Ubuntu overwritten by Windows 7"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by maruf7 on 2013-01-03
Hello,
I recently setup Windows 7 in my pc, thus my existing Ubuntu disappeared from boot menu. Is there any way to bring it back?

---

### Post by audiomick on 2013-01-03
That depends on exactly what you did. I think the best thing would be for you to go here

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

and follow the instructions to generate the Boot Info Summary. Don't use the boot repair yet.

Post the boot info summary here. That will show if the Ubuntu install perhaps still exists on the machine. If that is the case, then you can go on to try to get your boot back. I think the boot repair option of that tool should do this, or  maybe you will have to re-install grub manually.

If the Windows install really overwrote the Ubuntu install, you can't get it back. If this is the case, the boot info summary will definitely show this, so that is your first step. Find out what is really on the machine.

---

