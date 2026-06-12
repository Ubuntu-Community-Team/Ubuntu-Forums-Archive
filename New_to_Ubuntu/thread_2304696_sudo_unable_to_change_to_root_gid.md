---
title: "sudo: unable to change to root gid"
date: 2015-11-29
forum: New to Ubuntu
---

### Post by prakash14 on 2015-11-29
Hi All - Iam new to ubuntu.  I recently bought a dell laptop with pre installed ubuntu(14.04 lts). Iam trying to login to root. Iam not able to login. I tried pressing the shift while restarting the os to get into the recovery mode. But still iam not able to.

This laptop came with guest user, it doesnt have any privilages to do any of the tasks.

Please let me know what i need to do to solve my problem.

thanks
-Prakash.

---

### Post by flocculant on 2015-11-29
The root account is password disabled. That's normal. 

If the laptop has come from Dell with only a guest user then I would assume that they've also sent you paperwork which I would have to imagine includes how to setup the laptop from new. Read that or contact Dell.

---

### Post by grahammechanical on 2015-11-29
Suppliers of machines with Ubuntu pre-installed usually do what is called an OEM (Original Equipment Manufacturer) install.

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

They create a temporary oem user and password which allows the supplier to set up the machine with software. But at the next reboot the buyer should see the image at the bottom of that Wiki page

> Once the computer was shipped to the end user and he finally boots for  the first time he will be taken to the system setup wizard where he will  be able to set his location, keyboard layout, user name etc.

Regards.

---

