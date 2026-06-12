---
title: "initramfs"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-05-26
Hi,

Is there anyway to get around this initramfs screen. No matter what flavor of ubuntu I install once I update the install and reboot I am dropped into the initramfs screen. BTW I am using the wubi and virtual disk option.

This appears to be a bug if so please let me know.

thanks in advance,

---

### Post by spiderbatdad on 2008-05-26
Can't recall workaround I saw for this. It might be as simple as running sudo update-initramfs -u from the prompt.
Also there is a wubi sub-forum:[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

And this guide:[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

### Post by bikinguy77388 on 2008-05-26
Thanks! will ck it out.

---

### Post by LinuxFox on 2008-05-26
The BusyBox thing? That happened to me when I updated earlier too, and I'm also using Ubuntu via Wubi.  When Ubuntu is starting up press ESC during the countdown.  A menu appears telling you which Ubuntu kernel versions there are as well as Windows XP.  

I don't know about your computer (I'm using Ubuntu 8.04), but when I selected version 2.6.24.16 from the menu, it booted into Ubuntu, not BusyBox.

---

