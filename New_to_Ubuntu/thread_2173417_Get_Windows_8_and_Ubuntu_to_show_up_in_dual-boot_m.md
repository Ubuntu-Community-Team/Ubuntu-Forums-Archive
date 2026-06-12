---
title: "Get Windows 8 and Ubuntu to show up in dual-boot menu (separate hard drives)"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by charles10 on 2013-09-09
Dear all,

I have a Dell XPS8500 running Windows 8 Pro.  After many tries, I was able to install Ubuntu 12.04.3 from a CD onto a different hard drive.  Right now it boots up into Windows without giving me the option to use Ubuntu. However, if I change the boot device to the hard drive Ubuntu is on, it boots up without the option for Windows.  I'd like to have the option to chose (I don't care if its the Windows or Ubuntu OS chooser) an OS before boot without having to go into the bios to change the boot device.

Thank you for any help,
Charles

---

### Post by Petro Dawg on 2013-09-09
You might give Boot-Repair a try...

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by charles10 on 2013-09-09
I forgot to mention that.  I did use that and nothing appeared to change.  It gave the site [http://paste2.org/new-paste](http://paste2.org/new-paste).  I'll give the advanced settings a try to double check which hard drive it is using though.

---

### Post by ajgreeny on 2013-09-09
have you run the command sudo update-grub from your ubuntu install?  That should be all that is needed to add windows to the grub menu.

PS: Your link above goes to a new posting, not the pasted info you got from running boot-repair.

---

### Post by charles10 on 2013-09-09
I got it to work now.  my Ubuntu system crashed when I tried installing the nvidia drivers, so I had to redo it.  After reinstalling Ubuntu (it was in UFEI mode this time, the last time may have been legacy) I made a 2GB partition on my C drive to install grub to during the update and everything works fine (I can even use "fast startup" for Windows 8 without anything going wrong).

---

