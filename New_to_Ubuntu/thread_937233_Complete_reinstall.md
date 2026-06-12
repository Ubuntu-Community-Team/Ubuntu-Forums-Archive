---
title: "Complete reinstall"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-03
How can I do a complete reinstall of Ubuntu over a network? At the moment I have a ssh connection possibility.

---

### Post by shifty_powers on 2008-10-03
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

might be helpful

---

### Post by bodhi.zazen on 2008-10-03
If you have a spare partition, use debootstrap ...

Then after installing the base, chroot into the new installation, install a kernel, add any additional packages you need, and then add in / edit /boot/grub/menu.lst and (in the chroot) /etc/fstab (and probably networking as well).

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

