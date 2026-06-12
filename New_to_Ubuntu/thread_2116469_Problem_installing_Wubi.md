---
title: "Problem installing Wubi"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by Helldogify on 2013-02-15
So i have just gotten a new laptop with win 8 pre installed and i have grown to dislike it very much. So i decided to install ubuntu to overcome some of the problems i was having but everytime i install it using wubi it comes up a with a prompt saying that the file "wubildr.mbr" is either corrupt or missing and when i go to check its there. What should i do to solve this.

---

### Post by auxilium on 2013-02-15
Hi,

What version of Ubuntu are you trying to install?

---

### Post by bcbc on 2013-02-18
You cannot install Wubi on a system with Windows 8 preinstalled, because it uses UEFI with GPT disks and Wubi does not support this.

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system]("http://askubuntu.com/q/221835/14916")

You can register your "me too" on the bug report if you want to: [https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242)

---

### Post by Mark Phelps on 2013-02-18
> **Helldogify said:**
> So i have just gotten a new laptop with win 8 pre installed and i have grown to dislike it very much. 
If it's the new "Tiles" interface, then join the group of us that also dislike that.

If you click the Desktop Tile when in Win8, you will see an interface very much like the Win7 desktop.  IF you like that better, there are Start Menu products you can instal to make that change permanent.

For more info, you should visit a Win8 forum (eightforums.com).

---

