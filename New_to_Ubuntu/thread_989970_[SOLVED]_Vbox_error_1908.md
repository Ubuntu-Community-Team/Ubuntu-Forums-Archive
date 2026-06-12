---
title: "[SOLVED] Vbox error 1908"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by jon555 on 2008-11-22
I just installed it on ubuntu 8.4 from ad remove programs. Then mounted win 95, started and this error appeared.:confused:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by beno1990 on 2008-11-22
Virtual box requires kernel modules for virtualisation to run, which are available from the repos.

```
sudo apt-get install virtualbox-ose-modules-generic
```

---

### Post by jon555 on 2008-11-22
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

and found this solution

> go to system -->Administration---->Users and Groups

click on 'manage groups'

Scan down the list, there should be a group called 'vboxusers'. If there is, double click on it and make sure that your username is ticked so that you are a member of the group. If there is no group, create one by clicking on 'Add Group', typing vboxusers in the group name field and making sure that your user name is ticked so that you are a member. Then, log out and log back in again. When you a start your virtual machine, everything should work!
**But then I got new problem**
[IMG]http://img407.imageshack.us/my.php?image=ekranattelsbw9.jpg[/IMG][http://img407.imageshack.us/my.php?image=ekranattelsbw9.jpg]("http://img407.imageshack.us/my.php?image=ekranattelsbw9.jpg")

---

### Post by beno1990 on 2008-11-22
In Virtualbox, you need to set it to mount a CD/virtual hard drive image to boot from, otherwise you get a no boot media error message like that one.

---

### Post by jon555 on 2008-11-24
I guess the image is damaged. 
Thanks for help!

---

### Post by lev2000 on 2008-12-07
Hey All,

I have the same problem, despite the facts that:
- I've already installed virtualbox-ose + kernel (sudo apt-get install virtualbox-ose-modules-generic)
- I've already added myself to vboxusers group
- I've tried to modify the permisions with command "chmod 777 /dev/vboxdrv"

Now I got the same error message: "VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)."

Can you help me?

Thanks in advance!

---

