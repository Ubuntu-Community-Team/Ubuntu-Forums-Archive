---
title: "Boot-repair tool error"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by piredllama on 2014-11-03
Not sure if this is the right way to post this but...

Anyway, one day after installing a program and launching it the computer froze. After restarting it it goes to the Ubuntu load page then switches to the flashy curser in the top left. So I use boot-repair to try to fix it, but it says I get an error an the problem doesn't appear to be fixed since I can't even attempt a launch of the original install. I have tried Boot-repair twice, the first on the USB version and second using it through Ubuntu on USB. Here is the log: [http://paste.ubuntu.com/8810636/](http://paste.ubuntu.com/8810636/)

Any help is appreciated!

---

### Post by yancek on 2014-11-03
> 
Anyway, one day after installing a program and launching it the computer froze

Posting some info on what that program was might help.  I'm not familiar with the boot repair software but, looking at your output you have nothing in the Master Boot Record which is alright as it shows installation in EFI mode.  The problem with  that is that non of the Ubuntu efi files are in the EFI partition.  I did see the below output at the bottom of the repair script which may be significant as an incorrect option entry?

> chroot /media/ubuntu/58a0ca77-4413-4341-91eb-0547d354ff87 update-grub -y Unrecognized option `-y'

---

### Post by stalkingwolf on 2014-11-04
try running the recovery option then fix broken packages.

---

