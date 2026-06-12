---
title: "Ubuntu boot loop"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by alfredo5 on 2014-10-28
I installed 14.04 lts and it's in a boot loop. It's a new build and it's the only os on there. Msi mobo and amd processor. 
Thanks for the help

---

### Post by oldfred on 2014-10-28
Did you install in BIOS/CSM or UEFI boot mode?

These are now older so I do not know if they still apply?
 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

### Post by Penguin360 on 2014-10-28
I had a login loop issue several days ago and I followed this post to fix it: [http://ubuntuforums.org/showthread.php?t=2233593](http://ubuntuforums.org/showthread.php?t=2233593). The reply from deadflowr in the post fixed my issue.

---

### Post by alfredo5 on 2014-10-30
Tried it. Nothing. I read that others reported a bug with ubuntu and amd processors combined with msi mobo. I think it could be a hardware problem.

---

### Post by Bucky Ball on 2014-10-30
I've always had luck with ctl+alt+F1, login, delete .xauthority and iceauthority, reboot.

---

