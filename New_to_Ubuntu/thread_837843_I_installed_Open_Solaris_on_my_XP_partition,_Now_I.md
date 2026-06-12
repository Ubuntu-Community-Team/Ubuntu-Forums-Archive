---
title: "I installed Open Solaris on my XP partition, Now I can't boot Ubuntu."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Smuk Pige on 2008-06-22
Hey All,

I've been running Gutsy Gibbon and XP on my PC laptop, and I decided to replace the MS product with something else. I installed Open Solaris on the Windows partition and now there is no option in the Solaris grub (?) menu for Ubuntu. I mainly use Apple so I'm not that familiar with the "behind the curtain" stuff. If I reinstall Ubuntu, will it give me back my old boot menu or an I going to have to get "under the hood" and work with the terminal?

P.S. I'm running off the Ubuntu live CD and it is SLOOOW!

Thanks,
Saffi

---

### Post by cariboo on 2008-06-23
Grub is now located in your open solaris partiton you should be able to edit /boot/grub/menu.lst in open solaris, if you know what hard drive and partition Ubuntu is on, you can add your ubuntu and off you go.

I haven't used Open Solaris, but I'm pretty sure most of the commands are the same. Here is a linkt to a grub howto.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Jim

---

### Post by sharks on 2008-06-23
restore grub using Supergrubdisk.

---

