---
title: "Automatically boot to another OS?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by legolas_w on 2008-07-06
Hi
Thank you for reading my post
Is there any way to automatically boot to another operating system?
My default (first boot option) is Ubunut 8.04 but I need to schedule the computer to restart and load Windows in an specific time. problem is that I should be with the computer to choose windows from the list in order to make it load windows instead of loading Linux after the XX seconds interval.

I thought maybe a program is already developed to let the use choose which OS to load after the restart.


Thanks.

---

### Post by rraj.be on 2008-07-06
You can use start up manager

```
 sudo apt-get install startupmanager

```

here you can set up different timeouts

Specify default o/s to boot.

make your grub password protected.

Customize your grub look etc.

---

### Post by stoneybroke on 2008-07-06
You will have to change the boot loader that can be found at Filesystem>Boot>Grub and edit the file Menu.lst you will need to be a root user so in a terminal window enter sudo gedit then load in the boot file and edit and save that but make sure that you save a backup copy before you start I think you need to change the option root (hd0,0) to wherever your windows boot option is but I'm not 100% sure. 

Hope that helps

---

### Post by ET! on 2008-07-06
you will find the menu.lst in /boot. first make a backup of the menu.lst file. nearly at the end of the file you will find the list of boot options...copy the windows part of it and paste it at above all the other options..that ought do the trick

---

