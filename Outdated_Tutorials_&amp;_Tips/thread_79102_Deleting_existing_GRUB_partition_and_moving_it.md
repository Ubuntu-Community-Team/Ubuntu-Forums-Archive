---
title: "Deleting existing GRUB partition and moving it"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by zeroverse on 2005-10-19
Hi,

My GRUB situation is probably unique.

I have Windows XP install on hd0,0 (/dev/hda1)
I have Ubuntu Breezy installed on hd0,1 (/dev/hda2)
I have Kubuntu Breezy installed on hd0,3 (/dev/hda4)

Kubuntu is ok, but I prefer Ubuntu and want to erase the Kubuntu partition and reload GRUB for Ubuntu (default) and Windows XP.  Because Kubuntu is the last OS I've installed, if I try to erase the Kubuntu partition, I will lose my grub loader.

Unfortunately, in trying to "fix" the problem, I completely erased the /boot/grub directory from the Ubuntu, so please assume that this must be fully restored.

I have LIVE CD's if I need them (and I have tried many "solutions" from these forums...but none of them seem specific to my particular dilemna).

To clarify: I have NO grub directory in the Ubuntu partition (hd0,1)...so this must be restored...and I want to be able to delete the kubuntu partition (hd0,3) without it affecting GRUB.

Thanks in advance for you help.

---

### Post by aysiu on 2005-10-19
This may help:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by zeroverse on 2005-10-19
The solutions on that thread don't work for my situation.  But thanks.

The problem is, fromt he grub prompt, when i type "root (hd0,1)" it tell me "Error 22: No such partition" but the partition does exist.

---

