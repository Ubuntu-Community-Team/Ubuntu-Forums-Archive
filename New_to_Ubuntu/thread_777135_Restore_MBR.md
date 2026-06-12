---
title: "Restore MBR"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by roypk on 2008-05-01
Hi,

Is there something in Ubuntu to restore the MBR back to its original state before GRUB messed around with it?  This is in case I want to uninstall Ubuntu.  I'm duel booting XP and Ubuntu and I don't want to have problems booting up in Windows after I uninstall Ubuntu.  I'm a newbie and the other distro I've tried was OpenSuse 10.3.  It has the option to restore the MBR and that was what I used before wiping out SuSe.  I don't seem to find anything like that in Ubuntu.

Best regards,
Roy

---

### Post by scragar on 2008-05-01
you can't restore it from ubuntu, however windows offers you an option to do this from command prompt:```
fixmbr
```

---

### Post by mlentink on 2008-05-01
I don't know about any Ubuntu tools, but you can easily do that by booting up XP in recovery console and running fixmbr

---

### Post by celticbhoy on 2008-05-01
Try this page should do for you :-

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by kellemes on 2008-05-01
Always have a copy of [Super Grub Disk]("http://www.supergrubdisk.org/"). It can "fix" the MBR in case you killed it.

---

### Post by muteXe on 2008-05-01
Yeah the super grub disk is ace.  worked for me.

---

### Post by roypk on 2008-05-01
Thanks guys.  I thought I'd missed something.  I think I'll take a look at SuperGrub.

Best regards,
Roy

---

