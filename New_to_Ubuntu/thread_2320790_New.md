---
title: "New???"
date: 2016-04-17
forum: New to Ubuntu
---

### Post by Julian_Clayton on 2016-04-17
Hello, I'm so new - I haven't even installed Ubuntu yet.  My question is:  If I disconnect my Windows HD and connect a blank HD for installing Ubuntu, will I be able to dual boot later after installation and reconnection of my Windows HD?

---

### Post by grahammechanical on 2016-04-17
The answer is, Yes. But.

It makes a difference what version of Windows you have installed. If it is Windows 8 & upwards you need to follow the advice given here

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Even so, once you have re-connected the Windows drive you will need to tell Ubuntu about the existence of Windows. You do that by going into the BIOS/UEFI boot system settings utility and setting it to boot from the Ubuntu drive.

You then load Ubuntu and open a terminal & run this command

```
sudo update-grub
```

You will be asked to put in your user password. It will not be printed to the screen but it will be accepted and the command will run. Watch the printout to the screen. It should show the Linux boot loader (Grub) detecting the Windows boot loader on the other drive. Then as long as you boot from the Ubuntu drive you should get a boot menu that will let you load from Ubuntu or Windows.

Regards.

It is possible to install Linux/Ubuntu without disconnecting the existing Windows drive. It is a little more complicated to do. If you are interested in that method we can give advice.

Regards.

---

### Post by Julian_Clayton on 2016-04-20
Thank you Graham, this is just the right sort of answer I was hoping for.  Concise and thorough. :D

---

