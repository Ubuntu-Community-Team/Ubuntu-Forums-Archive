---
title: "I unintentionally locked my Sd card by password"
date: 2017-10-10
forum: New to Ubuntu
---

### Post by degranje on 2017-10-10
Please can annyboddy help me?

i make an locked sd card by password

 and now i can not see any more the sd card, not in Linux and not in W10, systemmanagment>discmanagement refuses when i insert the sd cart into my laptop

 is there is a command so i can unlock the sd card ???

 this is the command with i locked my sd card: 

sudo ./mmc32 lock_sd /dev/mmcblk0 C99A20843ED7D90B6801E49F2BC80277

---

### Post by ian-weisser on 2017-10-10
This has happened before:  [https://ubuntuforums.org/showthread.php?t=2338304](https://ubuntuforums.org/showthread.php?t=2338304)

---

### Post by mc4man on 2017-10-10
I suspect you did this - 
[http://cartechnology.co.uk/showthread.php?tid=19023](http://cartechnology.co.uk/showthread.php?tid=19023)

Note:
"Now lock the card by password, it's not possible to unlock it with normal MMC
Driver, You Need a patched version of the kernel to be Able to unlock it."

See here
[https://github.com/alcooper/mmc-password-utils/issues/1](https://github.com/alcooper/mmc-password-utils/issues/1)
[https://patchwork.kernel.org/patch/6441061/](https://patchwork.kernel.org/patch/6441061/)

Feels like more trouble than the sd is worth..

---

