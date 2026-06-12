---
title: "intall ubuntu and wubi - help"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by lirazrom on 2008-08-29
hi
i was trying to install ubuntu but got error 17
i set the bios as sain in other forums - didnt help
formated my whole computer and installed xp again - didnt help

installed wubi - but got command line with prompt of (grub)

tried to install on microsoft virtual pc - got error the thrown out


what to do?

---

### Post by swoll1980 on 2008-08-29
> **lirazrom said:**
> hi
i was trying to install ubuntu but got error 17
i set the bios as sain in other forums - didnt help
formated my whole computer and installed xp again - didnt help

installed wubi - but got command line with prompt of (grub)

tried to install on microsoft virtual pc - got error the thrown out


what to do?

Maybe [this]("http://ubuntuforums.org/showthread.php?t=442945") will help

---

### Post by nicedude on 2008-08-29
I would strongly suggest not using Wubi and instead setting up a dual boot machine where you can still have XP but you also will get a real Ubuntu install. Wubi is a way to run Linux inside of Windows and it hurts performance and also can cause other problems like with wireless adapter driver installs etc.

It is not hard to do if you just read one of the many guides on the net for how to do it.

---

### Post by lirazrom on 2008-08-29
i tried to do dual boot but i got error 17
and i allready read the bios set
but it didnt helped

---

### Post by nicedude on 2008-08-29
Error 17 indicates GRUB can't id the partition type. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

This can be a  bios based problem but more than likely I think it could also be due to you having multiple disks or USB flash drive plugged in while installing and you are having a error due to grub not looking at the right partition or drive for its files , I am not 100% on this but I think it could well be the case.

Here is a linux thread where people had the same problem and even though they are talking about an older version of Ubuntu the basics are the same.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

