---
title: "Switch to Linux or Vista Icon"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by ex-para on 2012-11-21
I have dual boot, 12.4 and Vista. Is it possible to have an icon on the desktop to switch to Linux if using Vista or vice versa as opposed to picking which OS to use at boot up.

---

### Post by 2F4U on 2012-11-21
You need to boot into each operating system, so you would need to have an icon to reboot. But you would still need to select the operating system to boot at the grub prompt.

---

### Post by mike555 on 2012-11-21
no , you must pick one to boot into.

---

### Post by Jamie_Edwards on 2012-11-21
As far as I know, that option is only available to Apple Mac users, They use an application called "Boot Camp". We PC users don't have that luxury, I've been wanting an app for this sort of thing since I shifted to Ubuntu, would make my gaming life so much easier XD

---

### Post by ex-para on 2012-11-22
Thanks for the replies,looks like it cant be done.
Thanks again.

---

### Post by Wim Sturkenboom on 2012-11-22
It should be possible in Ubuntu. It's simply a matter of changing the default in /boot/grub/grub.cfg and rebooting.

It possibly can be done in windows as well if you install support for the ext filesystem; it might be advisable in that case to use a separate boot partition formatted as ext2 (not sure what is supported).

---

### Post by mlentink on 2012-11-22
> **Jamie_Edwards said:**
> As far as I know, that option is only available to Apple Mac users, They use an application called "Boot Camp". We PC users don't have that luxury, I've been wanting an app for this sort of thing since I shifted to Ubuntu, would make my gaming life so much easier XD

AFAIK Boot camp isn't an application but a boot loader. At boot time, you will be given the option to boot either windows or osx, you can't start one from within the other. Perhaps you were referring to VMWare Fusion or Parallels?

---

### Post by AstroLlama on 2012-11-22
You can share drives, though, in this way the same partition can be accessed from each OS. You can have your files available to you. 

Another option is to make your power key set to reboot, or restart. this is usually the default, but not always the case. In fact that's what I do.

---

