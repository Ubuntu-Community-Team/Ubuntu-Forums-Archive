---
title: "Dual boot issues - GRUB disappears every time I boot Win 8.1"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by dave.ferrax on 2013-12-22
I installed Ubuntu 13.10 on my brand new Samsung Ultrabook s5 (NP535U3C) which came with Win 8 installed (I upgraded to 8.1 as soon as I got my hands on it)  a week ago and I'm having problems since then. Every time I boot into Windows via GRUB, selecting Windows Boot Manager from the menu, when I turn the laptop on again the next time, GRUB is vanished, and either I get the black screen which tells me to insert the boot device - and I can't boot at all, neither Windows nor Ubuntu - or, if i plug my USB stick I used to install Ubuntu, that menu you see when you install Ubuntu for the first time (try w/o installing, install, check disk for defects etc.). So every damned time I have to log into Windows for some reason, I have to reinstall GRUB with boot-repair from a live session. I did this like four times but nothing seems to be changing. What can I do for fixing this?

---

### Post by oldfred on 2013-12-22
Some have reported that this work around in Windows works for the new Windows. It seems to auto reset itself as first in UEFI boot every time.

 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

