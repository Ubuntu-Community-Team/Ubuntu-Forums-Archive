---
title: "Can't get into Recovery mode!"
date: 2015-06-26
forum: New to Ubuntu
---

### Post by woody6 on 2015-06-26
Hi all,

After a stupid mistake, I changed my password and now can't remember what I changed it to. I've found out that you can reset it by going into recovery mode, but I can't seem to get there! I have Ubuntu 14.04.2 running alongside OS X Yosemite on my MacBook Pro. I have the rEFInd boot manager installed, but I can delete it. I've tried holding Shift while booting any of the three (?) options to boot Ubuntu, and tried holding C as well. Whatever I do, I can't seem to get into recovery mode.

Here are the three options I get in rEFInd, as well as OS X:

Boot boot\vmlinux-3.16.0-41-generic from 14GiB ext4 volume
Boot boot\vmlinux-3.16.0-30-generic from 14GiB ext4 volume
Boot Linux from whole disk volume

Can anyone help me please? Bear in mind I can't run any sudo commands as I can't remember my password :P

Woody

---

### Post by grahammechanical on 2015-06-26
You need a way to edit the boot parameters. How to do that with rEFInd I cannot say. But if you can edit the boot parameters look for a line that has

> ro quiet splash

and edit it to

> ro recovery nomodeset

Regards.

---

### Post by woody6 on 2015-06-26
Sorry, I'm entirely new to Ubuntu and Linux and its entirety. Where can I find these boot parameters?

Woody

Edit: I've fixed it with the solution found on this page: [askubuntu.com/questions/641452/brand-new-to-ubuntu-cant-get-into-recovery-mode]("http://askubuntu.com/questions/641452/brand-new-to-ubuntu-cant-get-into-recovery-mode")

Woody

---

