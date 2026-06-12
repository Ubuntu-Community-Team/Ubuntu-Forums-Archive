---
title: "[SOLVED] messed with my graphics card now it wont boot"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by stufromscotland on 2008-07-19
I was trying to get desktop effects working following a thread. I changed the driver for my graphics card in screens and graphics. Now the laptop wont boot. It stops at "Running local boot scripts (etc/rc.local). 
Can someone help. Cheers

---

### Post by waspbr on 2008-07-19
right,

if you can get to your login screen then go to sessions and select the option fail-safe gnome.


if not, then back on grub(the boot up list thingy) select the system recovery option.I am assuming you are on hardy heron here. Anyway, select that , it should take you to a dialogue, there select the option fix xorg (or fix x, can't recall) this should be rather automatic. Then, while you are there, select also the second option, that is "fix broken packages" then try to resume booting.

it doesn't seem to me that you have broken your xorg... but anyway let us know how it goes

---

### Post by spiderbatdad on 2008-07-19
A link to the guide you were following or details regarding the changes you made might make it possible to help you.

Otherwise run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```to set your xserver settings back to where they were.

---

### Post by PmDematagoda on 2008-07-19
When the boot stops at a place like:-
```
Running local boot scripts (etc/rc.local)
```
that usually is an indication of a borked X-Server. To the OP, could you post the specifications of your PC? Also, if you have Ubuntu 8.04, boot Ubuntu in Recovery Mode and select xfix, after that is done see if the X-Server now works properly.

---

### Post by stufromscotland on 2008-07-19
Ok I did the dpkg thing and now it says it`s overwritten a custom configuration which I take is a good thing.
It says root@stu-laptop:~#
Now what?

---

### Post by spiderbatdad on 2008-07-19
reboot

---

### Post by stufromscotland on 2008-07-19
Thankyou. It`s fixed.

---

### Post by spiderbatdad on 2008-07-19
:) Linux can be a little tricky like that...after a successful command, generally a prompt is returned. No message jumps out and says, "command successful...You may now..." Generally if no error message is returned, commands you enter are "silently" carried out.

---

