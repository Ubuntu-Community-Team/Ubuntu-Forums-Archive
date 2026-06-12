---
title: "Can't log on"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Janade on 2013-02-01
(Ubuntu 12.04) After clicking on update. and shutting down the next time I tried to get on to my system I have not been able to do so. The Gru Grab screen come up. When I select the option:
Ubuntu, with Linux 3.2.0-36-generic
it boost up to a listing that ends with 
 
[ 13.9503491 CR2: fffffffffffffffffff8
 
If I shut down and then restart and choose the recovery mode it result in the 
[ 10.2926531 ----[ end trace d66fd9dadc060a37 ]----
 
I do not know how to get beyond thes points

---

### Post by Bashing-om on 2013-02-01
Janade; Hi !

What results ?
Grub menu -> "recovery mode" -> "fsck" ; upon completion of the file system check/repair -> "resume normal boot" -> GUI login.

Gui login : username and password -> desktop.

Reboot.

If you do not boot up, further investigation depends of the error conditions present at that time.
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-02-01
Try booting into an earlier kernel. The Linux 3.2.0-36 was part of that update. Well, it was on my machine.

Try booting into Linux 3.2.0-35 or anything lower than -36 and see what happens.

If you get to a desktop, then avoid 3.2.0-36 until you have done a few updates over then few days. You mat get a fix for that kernel.

Regards.

---

### Post by Impavidus on 2013-02-01
3.2.0-36? I installed -37 today. There may be a few days difference between different mirrors, but you can expect -37 shortly.

---

