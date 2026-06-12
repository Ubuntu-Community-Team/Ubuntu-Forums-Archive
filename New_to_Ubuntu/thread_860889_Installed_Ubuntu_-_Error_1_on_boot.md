---
title: "Installed Ubuntu - Error 1 on boot"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by TheBana on 2008-07-16
Hi,

I recently installed Ubuntu and when I come to boot it I get an error 1 message "Pathname must be blocklist or absolute".

I've done some Googling and apparently it has something to do with my menu.lst? However, I'm extremely new to Linux / Ubuntu and have no idea what I need to do.

I have two hard drives, one is 40gb with XP installed on it ( C: ). The other 120gb, 36gb clean partition on which I installed Ubuntu in XP from the Live CD ( G: ), and a 80gb partition for general stuff, video files, music etc ( F: ).

What do I need to do in order to get Ubunutu working? It worked when running it straight off the CD.

If you need any more information let me know.

---

### Post by kansasnoob on 2008-07-16
I'm not absolutely sure of this, but maybe BIOS is booting the Windows drive first (or trying to) and can't find the GRUB file system. So maybe, just maybe, changing which hard drive boots first in BIOS may be what's needed.

If you're familiar with BIOS settings it can't hurt to try, otherwise wait for a second opinion, OK?

---

### Post by louieb on 2008-07-16
> **TheBana said:**
> Hi,...I installed Ubuntu in XP from the Live CD...

Sounds like you did a** wubi** install.  Might have better luck finding a solution to the problem in the [wubi section of the forum .]("http://ubuntuforums.org/forumdisplay.php?f=234")

---

### Post by TheBana on 2008-07-16
Yep, it seems as though I did do a Wubi install. I'll try the latest installer after trying to boot order in the BIOS.

Thanks

---

