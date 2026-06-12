---
title: "[SOLVED] Reinstalled Winxp and lost Grub bootloader"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by STFU Donny on 2008-05-27
Hello. I used to have a dual boot setup with windows xp and Xubunu on my laptop. I reinstalled windows xp and now I've lost grub and my dual boot menu. Xubuntu is still installed on a separate partition. How can I get this back?

Thanks

---

### Post by phoenix_abhi on 2008-05-27
Put ur Live CD in and reboot.
Go to the terminal and type
sudo grub
find /boot/grub/stage1
this will show which is ur Linux partition

grub> root (hd0,1)
grub> setup (hd0)
grub> quit

reboot ur Grub is reloaded

The hd0 is the number of hardisk u have. If only one it is 0
(hd0,1) the 1 here is ur linux partition

---

### Post by Joeb454 on 2008-05-27
Have you tried looking at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It guides you through the steps of reinstalling GRUB (I used it before)

---

### Post by sayakb on 2008-05-27
You might also try Supergrub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by STFU Donny on 2008-05-28
> **Joeb454 said:**
> Have you tried looking at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It guides you through the steps of reinstalling GRUB (I used it before)

This seems to have worked as I'm posting from xubuntu! Thanks.

How do I mark as solved?

---

### Post by pjnsmb on 2008-05-29
should be under "thread tools" (in red) at the top of the page.............

cheers

---

