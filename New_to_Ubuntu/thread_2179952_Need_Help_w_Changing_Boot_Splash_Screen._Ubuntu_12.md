---
title: "Need Help w/ Changing Boot Splash Screen. Ubuntu 12.04"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by MzX3WJM on 2013-10-10
---Problem has been solved---
Hello all. I have looked up some various threads and tried a couple GUI resources to change my Splash screen. It loads correctly when I shut my computer down or do a restart, but not when it turns on initially. 

I believe it might have something to do with this, but not 100% sure. Still am a Newbie afterall. 

Press enter to keep the current choice
[*], or type selection number: 2
john@john-Lenovo-B590:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.5.0-42-generic
/usr/sbin/mkinitramfs: 1: /etc/initramfs-tools/conf.d/splash: --2013-10-10: not found
/usr/sbin/mkinitramfs: 2: /etc/initramfs-tools/conf.d/splash: Syntax error: "(" unexpected

And thanks to anyone who can possibly help me!

Also thought I'd add a bit more to description; main issue here is that it still displays the ubuntu splash screen when i turn the computer on however it displays the correct theme as i restart & or shutdown.
Any advice, tips, or ideas would greatly be appreciated. Once again thanks! :)

Solved Problem.

---

