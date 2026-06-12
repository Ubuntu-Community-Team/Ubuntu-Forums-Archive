---
title: "Install fedora alongside ubuntu without removing GRUB"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by kmegamind on 2013-07-19
I have Ubuntu along side Windows 7 and i want to install fedora alongside both, now i love the ububtu grub and i don't want the fedora grub to appear instead of ubuntu's grub
how can i do that ?

---

### Post by ajgreeny on 2013-07-19
I am sure that at some point in installing Fedora there is an option regarding where the bootmanager (grub) will be installed, or perhaps not installed at all, but it is a long time since I tried fedora and I can't remember the detail.

Assuming you get the option at some point, you can safely choose to not install grub at all, and let ubuntu grub do all the booting. You will need to boot to ubuntu and run sudo update-grub to add fedora to ubuntu's grub menu, but I think I have read somewhere that you must mount the fedora partition in ubuntu before running the grub update or it will not find fedora.

If you can't choose not to install grub, you will need to install it to the root partition of fedora instead of the normal root of the disk, ie install to /dev/sda3 (or whichever partition is correct) and not to /dev/sda

Watch out for the default of fedora to install to LVM partitions, which used to mean that ubuntu could not see it without a few LVM package additions, details of which I will have to leave for you to search out.

---

### Post by oldfred on 2013-07-19
Some do not use the default of LVM with Fedora and just install to a standard LInux formatted partition. Then there are fewer issues multi-booting. The standard LVM may make sense if installing only Fedora or if drive is totally LVM. But that adds a level of complications.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

